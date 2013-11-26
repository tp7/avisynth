
AviSynth Syntax - Internal functions
------------------------------------

In addition to `internal filters`_ AviSynth has a fairly large number of
other (non-clip) internal functions. The input or/and output of these
functions are not clips, but some other variables which can be used in a
script. They are roughly classified as follows:

-   `Boolean functions`_

They return true or false, if the condition that they test holds or not,
respectively.

-   `Control functions`_

They facilitate flow of control (loading of scripts, arguments checks, global
settings adjustment, etc.).

-   `Conversion functions`_

They convert between different types.

-   `Numeric functions`_

They provide common mathematical operations on numeric variables.

-   `Runtime functions`_

These are internal functions which are evaluated at every frame. They can be
used inside the scripts passed to runtime filters (`ConditionalFilter`_,
`ScriptClip`_, `FrameEvaluate`_) to return information for a frame.

-   `Script functions`_

They provide AviSynth script information.

-   `String functions`_

They provide common operations on string variables.

-   `Version functions`_

They provide AviSynth version information.

$Date: 2011/01/16 12:24:09 $

.. _internal filters: corefilters.htm (Internal filters)
.. _Boolean     functions: syntax_internal_functions_boolean.htm
    (Internal functions/Boolean functions)
.. _Control     functions: syntax_internal_functions_control.htm
    (Internal functions/Control functions)
.. _Conversion     functions: syntax_internal_functions_conversion.htm
    (Internal functions/Conversion functions)
.. _Numeric     functions: syntax_internal_functions_numeric.htm
    (Internal functions/Numeric functions)
.. _Runtime     functions: syntax_internal_functions_runtime.htm
    (Internal functions/Runtime functions)
.. _ConditionalFilter: corefilters/conditionalfilter.htm
    (ConditionalFilter)
.. _ScriptClip: corefilters/conditionalfilter.htm (ScriptClip)
.. _FrameEvaluate: corefilters/conditionalfilter.htm (FrameEvaluate)
.. _Script     functions: syntax_internal_functions_script.htm (Internal
    functions/Script functions)
.. _String     functions: syntax_internal_functions_string.htm (Internal
    functions/String functions)
.. _Version     functions: syntax_internal_functions_version.htm
    (Internal functions/Version functions)
