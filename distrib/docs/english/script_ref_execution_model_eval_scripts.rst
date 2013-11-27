
The script execution model - Evaluation of runtime scripts
----------------------------------------------------------

Evaluation of runtime scripts starts, as already stated, at the frame serving
phase of the main script's execution. At that point frames of the final
output clip are requested by the host video application. This triggers a
sequence of successive calls to the GetFrame / GetAudio methods of all
filters along the filter graph. Whenever one of those filters is a runtime
filter, the following three-phase sequence of events happens *in every
frame*:

-   Runtime environment initialisation.
-   Runtime script parsing and evaluation.
-   Runtime environment cleanup and delivery of the resulting frame.

The following paragraphs examine each phase in more detail.


Contents
--------

-   `1`_ ` Runtime environment initialisation`_
-   `2 Runtime script parsing and evaluation`_
-   `3 Runtime environment cleanup and delivery of the resulting frame`_
-   `4 The runtime environment in detail`_

    -   `4.1 Elements of the runtime environment`_
    -   `4.2 Runtime functions and current_frame`_
    -   `4.3 Checklist for developing correct runtime scripts`_


Runtime environment initialisation
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

The runtime filter code sets (at the top-level script local scope) its
`special variables`_ for the runtime script. These at the minimum include
``last``, which is set to the filter's source clip and ``current_frame``,
which is set to the frame number requested by the filter from the AviSynth
code.

As a consequence, those special variables *cannot* be passed between runtime
scripts; whatever value the passing script will set, it will be overwritten
by the receiving filter's frame initialisation code.


Runtime script parsing and evaluation
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

The runtime script is parsed, as a regular script would be parsed if loaded
in AviSynth. The parsing mechanism is the same. Thus *everything* allowed to
a regular script is allowed to a runtime script; *what changes is the context
of execution*. For example, you can:

-   Use **multi-line scripts**; they just have to be contained inside a
    three-double-quotes pair (this is a requirement only if string literals
    are used inside the script, else single double quotes can be used also).
-   Define / assign variables, both local and global.
-   `Import`_ other scripts and/or load plugins and/or define functions.
-   Call functions and filters.
-   Use `arrays`_ and `block statements`_.
-   Use `control structures`_.

Of course, some of the above are **not advisable**, because the different
execution context poses different constrains regarding performance and
resource usage. The main rule of thumb here is: **Parsing occurs in every
frame requested. Therefore, computationally expensive actions should be
avoided**. More on the `performance considerations`_ section.


Runtime environment cleanup and delivery of the resulting frame
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

The runtime filter code receives the result of script parsing and evaluation.
If all went well, the result will be a valid filter graph (the runtime filter
graph) from which the runtime filter requests to fetch the needed frame. If
not, the filter will propagate the error to the caller. When the filter's
code will return the final video frame, the runtime filter graph will be
destroyed. As part of the cleanup the runtime filter code also restores the
``last`` special variable to its previous value.


The runtime environment in detail
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Despite the very thin layer of added features (just a handful of variables
and functions) the runtime environment is much more dynamic that the normal
(main) script environment. The *key-difference* is the event-driven model of
runtime script execution as opposed to the linear flow of the main script's
execution. Execution of a runtime script occurs only in the event of a frame
request. In addition, since intermediate filters in the chain may shuffle and
combine frames in an arbitrary fashion, the requested frame's number may be
different than the final clip's frame number.


Elements of the runtime environment
:::::::::::::::::::::::::::::::::::

At any time during the frame serving phase, the elements of the runtime
environment are the following:

-   The environment inherited by the main script's parsing phase, that is
    the main script's top-level local variables, the global variables and all
    imported script and plugin functions.
-   The `special variables`_ set on every frame by the runtime filter
    initialisation code (``last``, ``current_frame``, etc.)
-   A set of `runtime functions`_ to assist common information extraction
    operations.
-   The environment created by the successive evaluation of runtime
    scripts triggered by all the final output clip's frames that have been
    requested so far by the host video application. This may include
    modifications to the environment inherited by the parsing phase such as
    change of variables' values, as well as addition of new locals and
    globals.


Runtime functions and current_frame
:::::::::::::::::::::::::::::::::::

An interesting feature of `runtime functions`_ is that they consult the value
of the ``current_frame`` special variable in order to determine what frame of
their input clip(s) to inspect for extracting information. This provides the
ability inside a runtime script to easily request information for *any* frame
of a clip by changing before the call to the function the ``current_frame``
variable.

As explained above, setting the ``current_frame`` variable has no effect on
other runtime scripts in the filter chain because the runtime filters'
initialisation code resets ``current_frame`` to the proper value before
executing the runtime script. It also has no effect on subsequent filter
calls in the runtime script. But it does have on runtime functions and
anywhere the value of ``current_frame`` is used. Therefore, after such a
usage it is good practice to restore the variable to its initial value before
issuing other script commands.

A skeleton example of a runtime script that computes a weighted second order
luma interpolation value (the actions after the computation are omitted)
follows:

::...previous processing omitted...
    `ScriptClip`_("""  # this is a multiline string
        n = current_frame
        lm_k = `AverageLuma`_()
        current_frame = n - 1
        lm_km1 = AverageLuma()
        current_frame = n + 1
        lm_kp1 = AverageLuma()
        dvg = (lm_km1 - 2 * lm_k + lm_kp1) / 2
        lm_ipl = lm_k + `Sign`_(dvg) * `Sqrt`_(`Abs`_(dvg))
        current_frame = n # remember to reset current_frame
        ...rest of script omitted...
        """)
    ...subsequent processing omitted...
Checklist for developing correct runtime scripts
::::::::::::::::::::::::::::::::::::::::::::::::

Despite the dynamic nature of the runtime environment, creating runtime
scripts is relatively easy if you follow a simple set of rules:

-   Remember that your input (source) clip is stored upon start of script
    execution in the ``last`` special variable.
-   If you assign temporary clips to variables, remember to set ``last``
    at the end or issue a ``return`` statement.
-   Do not change (with respect to the source clip of the filter) the
    dimensions, colorspace or framerate of the final result.
-   Do not assume - unless there is a **very** compelling performance-
    related reason- a particular ordering of frame requests; try to build
    ordering-neutral scripts, that depend only on ``current_frame``.
-   Inspect the names of all input variables (ie those variables that are
    *not initialised* to a value inside the runtime script) of your runtime
    scripts to ensure that they are not overridden accidentally by a normal,
    not used for inter-script communication variable in any runtime script
    along the chain.
-   In particular, avoid putting inside `functions`_ calls to runtime
    filters that share state between invocations or with other filters
    through variables; it is easy to forget that *you may only call the
    function once*, else you will end up with multiple filters that share
    *the same* variables, thus with a bug in your script.

In view of the above, runtime filters should be used in functions only if
they either:

-   do not share state between invocations or with other filters through
    variables, or
-   the function code takes care to create *unique names *of all the
    runtime script's shared variables on each function invocation.

A way to avoid variables is to dynamically build the runtime script using
string concatenation and assign the related arguments' values to local
variables in the runtime script. See the example code of the `bracket_luma`_
function.

--------

Back to the `script execution model`_.

$Date: 2011/04/29 20:11:14 $

.. _1: #Runtime_environment_initialisation
.. _Runtime script parsing and evaluation:
    #Runtime_script_parsing_and_evaluation
.. _Runtime environment cleanup and delivery of the     resulting frame:
    #Runtime_environment_cleanup_and_delivery_of_the_resulting_frame
.. _The runtime environment in detail: #The_runtime_environment_in_detail
.. _Elements of the runtime environment:
    #Elements_of_the_runtime_environment
.. _Runtime functions and current_frame:
    #Runtime_functions_and_current_frame
.. _Checklist for developing correct runtime scripts:
    #Checklist_for_developing_correct_runtime_scripts
.. _special variables: syntax_runtime_environment.htm (Runtime
    environment)
.. _Import: corefilters/import.htm (Import)
.. _arrays: script_ref_arrays.htm (Arrays)
.. _block     statements: script_ref_block_statements.htm (Block
    statements)
.. _control     structures: syntax_control_structures.htm (Control
    structures)
.. _performance considerations: script_ref_execution_model.htm (The
    script execution model)
.. _runtime     functions: syntax_internal_functions_runtime.htm
    (Internal functions/Runtime functions)
.. _ScriptClip: corefilters/conditionalfilter.htm (ScriptClip)
.. _Sign: syntax_internal_functions_numeric.htm
.. _functions: syntax_userdefined_scriptfunctions.htm (Script functions)
.. _bracket_luma: script_ref_execution_model_lifetime_variables.htm
    (title)
