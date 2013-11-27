
The script execution model - Sequence of events
-----------------------------------------------

The sequence of events that occur when you execute (ie load and render to
your favorite encoder) an AviSynth script is presented below. The sequence is
conseptualy divided in three major phases:

1.  `Initialisation phase`_
2.  `Script loading and parsing phase`_
3.  `The video frames serving phase`_


The initialisation phase
~~~~~~~~~~~~~~~~~~~~~~~~

During this phase the following events occur:

-   An AVI stream object is created by the operating system, using the
    handler code provided by AviSynth.
-   AviSynth dll is loaded and performs (among other initialization
    actions) auto-loading of the following files that are placed in the
    AviSynth autoload folder:

    -   All AviSynth plugins (files with ``.dll`` extension).
    -   All AviSynth include scripts (files with ``.avsi`` extension).

During auto-loading:

-   The plugin and script functions are registered in the internal data
    structures of AviSynth; all plugins are unloaded after this phase. Only
    if a function is actually used inside the script, the plugin is loaded
    again.
-   Avisynth include scripts are parsed (executed), as if they where all
    included in the top of the script source code with `Import`_ statements.


The script loading and parsing phase
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

During this phase the following events occur:

-   The host video application (the editor or the encoder) requests a
    frame from the AVI stream object (usually frame 0, but you should not
    count on this always being true).
-   The script is loaded with a call to the Import `internal function`_
    and its contents are passed to the Eval() `control function`_ for
    parsing.
-   The entire parse process takes place. `Expressions`_ are evaluated,
    `variables`_ are set and clips are created and chained together to form
    the script's fitler graph (see next section).
-   At this point, just after the end of the parse process:

    -   The filter graph has been formed.
    -   Global variables have attained their final (regarding the parsing
    phase) values and, along with all functions defined in the script or
    imported in the global scope, are available for use and possibly
    **modification** by the runtime scripts.


The video frames serving phase
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

During this phase the following events occur:

-   The initially requested frame is delivered to the host application.
    This forces runtime scripts that are possibly included in the source code
    to be parsed (executed) for that frame.
-   The host video application requests additional frames. Each frame is
    delivered, possibly forcing runtime scripts that are in the filter chain
    for that frame to be parsed (executed).

**Note:** since runtime scripts may be anywhere in the filter chain and
frames may be shuffled (AviSynth is an NLE after all!) the statement "for
that frame" should be interpreted as "for that frame of the final clip and
any linked frames of intermediate clips".

--------

Back to the `script execution model`_.

$Date: 2010/11/28 18:47:26 $

.. _Initialisation phase: #The_initialisation_phase
.. _Script loading and parsing     phase:
    #The_script_loading_and_parsing_phase
.. _The video frames serving phase: #The_video_frames_serving_phase
.. _Import: corefilters/import.htm (Import)
.. _internal     function: syntax_internal_functions.htm (Internal
    functions)
.. _control     function: syntax_internal_functions_control.htm (Internal
    functions/Control functions)
.. _Expressions: syntax_ref.htm (AviSynth Syntax)
.. _variables: syntax_script_variables.htm (Script variables)
.. _script execution model: script_ref_execution_model.htm (The script
    execution model)
