
AviSynth Runtime environment
----------------------------


Contents
~~~~~~~~

-   `1 Definition`_
-   `2 Runtime filters`_
-   `3 Special runtime variables and functions`_
-   `4 How to script inside the runtime environment`_


Definition
~~~~~~~~~~

The runtime environment is an extension to the normal AviSynth script
execution environment that is available to scripts executed by `runtime
filters`_. Its basic characteristic is that the runtime filters' scripts are
evaluated (compiled) **at every frame**. This allows for complex video
processing that it would be difficult or impossible to perform in a normal
AviSynth script.

Let's now look at the above definition in more detail. The runtime
environment is:

1.  An environment, that is a set of available local and global variables
    and filters / functions to be used by the script.
2.  An extension to the normal AviSynth script execution environment;
    that is there are additional variables and functions available to runtime
    scripts.
3.  Available to scripts executed by runtime filters **only**, that is
    scripts inside it are executed only during the AviSynth "runtime" (the
    frame serving phase).

The last is the biggest difference. Normal script code is parsed and
evaluated (compiled) at the start of the script's `execution`_ (the parsing
phase) in a linear fashion, from top to bottom; the result is the creation of
a `filter graph`_ that is used by AviSynth to serve frames to the host video
application. Runtime script code is executed *after* the parsing phase, when
frames are served. Moreover it is compiled on every frame requested and only
for that specific frame, in an event-driven fashion.

**Note:** Audio is *not* handled by the runtime environment; it is passed
through untouched. This also means that you cannot modify clip audio with
runtime filters.


Runtime filters
~~~~~~~~~~~~~~~

The following `filters`_ are the basic set of the so-called "runtime
filters":

-   `ConditionalFilter`_: Selects, on every frame, from one of two
    (provided) filters based on the evaluation of a conditional expression.
-   `ScriptClip`_: Compiles arbitrary script code on every frame and
    returns a clip.
-   `FrameEvaluate`_: Compiles arbitrary script code on every frame but
    the filter's output is ignored.
-   `ConditionalReader`_: Loads input from an external file to a
    selectable `variable`_ on every frame.

In addition, the `WriteFile`_ filter can also be considered a runtime filter,
because it sets the special variables set by all runtime filters before
evaluating the expressions passed to it, which can use the special `runtime
functions`_.


Special runtime variables and functions
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

All runtime filters set and make available to runtime scripts the following
special variables.

-   last: The clip passed as argument to the filter
-   current_frame: The frame number (ranging from zero to input clip's
    `Framecount`_ minus one) of the requested frame.

All the above variables are defined at the `top-level script local scope`_.
That is you read and write to them in a runtime script as if they where
variables that you declare at the script level.

Runtime scripts can also call a rich set of `special functions`_ that provide
various pieces of information for the current frame of their input clip.


How to script inside the runtime environment
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Using the runtime environment is simple: you use one of the `runtime
filters`_ and supply it with the needed arguments. Among them, two are the
most important:

-   The input clip
-   The runtime script

The latter is supplied as a string argument which contains the AviSynth
script commands. Scripts can contain many statements (you can use a multiline
string), local and global variables and function calls, as well as special
`runtime functions`_ and `variables`_. In general all statements of the
AviSynth `syntax`_ are permitted, but attention must be paid to avoid overly
complex scripts because this has a penalty on speed that is paid at **every
frame**. See the runtime section of `scripting reference`_'s `performance
considerations`_ for details.

Let's see a few examples:

::TODO...EXAMPLES

--------

Other points:

-   `Runtime functions`_ and variables, such as current_frame,
    AverageLuma(), etc., are available only at the runtime script's scope. To
    use them in a function you must pass them as arguments.
-   You can include an explicit ``return`` statement in your runtime
    script to return a clip that is not contained in the special ``last``
    variable.

--------

Back to `AviSynth Syntax`_.

$Date: 2008/12/07 15:46:17 $

.. _Definition: #Definition
.. _Runtime filters: #Runtime_filters
.. _Special runtime variables and functions:
    #Special_runtime_variables_and_functions
.. _How to script inside the runtime environment:
    #How_to_script_inside_the_runtime_environment
.. _runtime filters: #Runtime_filters (title)
.. _execution: script_ref_execution_model_sequence_events.htm (The script
    execution model/Sequence of events)
.. _filter graph: script_ref_execution_model_filter_graph.htm (The script
    execution model/The filter graph)
.. _filters: corefilters.htm (Internal filters)
.. _ConditionalFilter: corefilters/conditionalfilter.htm
    (ConditionalFilter)
.. _ScriptClip: corefilters/conditionalfilter.htm (ScriptClip)
.. _FrameEvaluate: corefilters/conditionalfilter.htm (FrameEvaluate)
.. _ConditionalReader: corefilters/conditionalreader.htm
    (ConditionalReader)
.. _variable: syntax_script_variables.htm (Script variables)
.. _WriteFile: corefilters/write.htm (WriteFile)
.. _runtime functions: syntax_internal_functions_runtime.htm (Internal
    functions/Runtime functions)
.. _Framecount: syntax_clip_properties.htm (Clip properties)
.. _top-level script local scope:
    script_ref_execution_model_lifetime_variables.htm (The script execution
    model/Scope and lifetime of variables)
.. _variables: #Special_runtime_variables_and_functions (title)
.. _syntax: syntax.htm (AviSynth Syntax)
.. _scripting reference: script_ref.htm (Scripting reference)
.. _performance considerations: script_ref_execution_model_perf_cons.htm
    (The script execution model/Performance considerations)
