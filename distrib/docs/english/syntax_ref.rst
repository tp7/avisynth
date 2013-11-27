
AviSynth Syntax
---------------

All basic AviSynth scripting statements have one of these forms:

1.  *variable_name* = *expression*
2.  *expression*
3.  **return** *expression*

(Two higher-level constructs also exist - the `function declaration`_ and the
`try..catch statement`_.)

In the first case, *expression* is evaluated and the result is assigned to
*variable_name*. In the second case, *expression* is evaluated and the
result, if a clip, is assigned to the special variable **last**. In the third
case, *expression* is evaluated and is used as the "return value" of the
active script block--that is either a function or the entire script. In the
latter case, the return value is typically the video clip that will be seen
by the application which opens the AVS file. As a shorthand, a bare
expression as the final statement in a script (or script block) is treated as
if the keyword **return** was present.

Most of the time the result of an expression will be a video clip; however an
expression's result can be of any type supported by the scripting language
(clip, int, float, bool, string) and this is how utility functions such as
`internal script functions`_ operate.

An *expression* can have one of these forms:

1.  *numeric_constant*, *string_constant* or *boolean_constant*
2.  *variable_name* or *clip_property*
3.  *Function*(*args*)
4.  *expression*.*Function*(*args*)
5.  *expression1* **operator** *expression2*
6.  *bool_expression* ? *expression1* : *expression2*

In the first case, the value of the *expression* is the value of the
constant. In the second case, the values correspond to `clip properties`_ or
`script variables`_ (which must have been previously initialized). In the
third case, the value is the return value of an AVS function (see below). The
fourth case is an alternate syntax (called "OOP notation") which is
equivalent to *Function*(*expression*, *args*).

The final two cases show that one can manipulate expressions using all of the
usual arithmetic and logical `operators`_ (from C) as you'd expect on ints,
floats and bools, as well as execute code conditionally with the ternary
operator. Strings can be compared with relational operators and concatenated
with '+'. The following operators are also defined on video clips: **a + b**
is equivalent to `UnalignedSplice`_(*a*, *b*), and **a ++ b** is equivalent
to `AlignedSplice`_(*a*, *b*).

The functions in AviSynth's scripting language are, by and large, video
filters. Although a function can return any type it chooses (this is a useful
feature for creating utility code to reuse in scripts; you can define your
own `script functions`_) functions which do **not** return a **clip** are
always limited to intermediate processing of variables to pass as arguments
to filters (functions that *do* return a clip). The script should always
return a clip as its final value. After all, AviSynth is a video processing
application.

Functions can take up to sixty arguments (hope that's enough), and the return
value can be of any type supported by the scripting language (clip, int,
float, bool, string). Functions always produce a new value and never modify
an existing one. What that means is that all arguments to a function are
passed "by value" and not "by reference"; in order to alter a variable's
value in AviSynth script language you must assign to it a new value.

To see the syntax of the function call for each built-in filter, view the
`internal filters`_. There are also built-in `internal functions`_ that
perform common operations on non-clip variables.

*Args* is a list of function arguments separated by commas. The list can be
empty. Each argument must be an expression whose type (eg text string,
integer, floating-point number, boolean value or video clip) matches the one
expected by the function. If the function expects a video clip as its first
argument, and that argument is not supplied, then the clip in the special
variable *last* will be used.

AviSynth functions can take named arguments. The named arguments can be
specified in any order, and the filter will choose default values for any
that you leave off. This makes certain filters much easier to use. For
example, you can now write **`Subtitle`_("Hello, World!", text_color=$00FF00,
x=100, y=200)** instead of **`Subtitle`_("Hello, World!", 100, 200, 0,
999999, "Arial", 24, $00FF00)**. `Colors`_ can be specified in hexadecimal as
in the example above or in decimal. In both cases it should be specified as
RGB value, even if the clip itself is YUV.

If no arguments are being passed to the function, you can also make the
function call without parentheses, e.g. **FilterName**. The primary reason
for this is to retain compatibility with old scripts. However, it's sometimes
convenient to leave off the parentheses when there's no possibility of
confusion.

Avisynth ignores anything from a # character to the end of that line. This
can be used to add **comments** to a script.

::# comment

In v2.58 it is possible to add **block** and **nested block** comments in the
following way:

::# block comment:
    /*
    comment 1
    comment 2
    */ ::# nested block comments:
    [* [* a meaningful example will follow later :) *] *]

Avisynth ignores anything from an __END__ keyword (with double underscores)
to the end of the script file. This can be used to disable some last commands
of script.

::`Version`_()
    __END__
    `ReduceBy2`_()
    Result is not reduced and we can write any text here

Avisynth **ignores case**: aViSouRCe is just as good as AVISource.

Multiple Avisynth statements on a single line can only be achieved in the
context of OOP notation or embedding filters as parameters of another
function such as:

::`AviSource`_("c:\video.avi").`Trim`_(0, 499)
    -or-
    `AudioDub`_(AviSource("c:\video.avi"), `WavSource`_("c:\audio.wav"))

Avisynth statements can be split across multiple lines by placing a backslash
("\") either as the last non-space character of the line being extended, or
as the first non-space character on the next line.

Line splitting examples (both valid and equal):

::Subtitle("Hello, World!", 100, 200, 0, \
      999999, "Arial", 24, $00FF00)

-or-

::Subtitle("Hello, World!", 100, 200, 0,
      \ 999999, "Arial", 24, $00FF00)

When splitting across multiple lines you may *place comments only at the end
of the last line*. Mixing comments with backslashes at an intermediate line
of the line-split will either produce an error message or result at hard to
trace bugs.

Example of a not-signaled bug by improper mixing of comments and line
separation:

::`ColorBars`_
    `ShowFrameNumber`_
    Trim(0,9) # select some frames  \
      + Trim(20,29)

The above example does not return frames [0..9,20..29] as intended because
the "\" is masked by the "#" character before it; thus the line continuation
never happens.

$Date: 2008/12/21 09:23:02 $

.. _function declaration: syntax_userdefined_scriptfunctions.htm (User
    defined script functions)
.. _try..catch statement: syntax_control_structures.htm (Control
    structures)
.. _internal script functions: syntax_internal_functions.htm (Internal
    functions)
.. _clip properties: syntax_clip_properties.htm (Clip properties)
.. _script variables: syntax_script_variables.htm (Script variables)
.. _operators: syntax_operators.htm (Operators)
.. _UnalignedSplice: corefilters/splice.htm (Splice)
.. _internal filters: corefilters.htm (Internal filters)
.. _Subtitle: corefilters/subtitle.htm (Subtitle)
.. _Colors: syntax_colors.htm (Colors)
.. _Version: corefilters/version.htm
.. _ReduceBy2: corefilters/reduceby2.htm
.. _AviSource: corefilters/avisource.htm (AviSource)
.. _Trim: corefilters/trim.htm (Trim)
.. _AudioDub: corefilters/audiodub.htm (AudioDub)
.. _ColorBars: corefilters/colorbars.htm (ColorBars)
.. _ShowFrameNumber: corefilters/showframes.htm (ShowFrameNumber)
