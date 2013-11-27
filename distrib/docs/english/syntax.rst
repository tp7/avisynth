
Getting started
---------------

Basically, AviSynth works like this: First, you create a simple text document
with special commands, called a script. These commands make references to one
or more videos and the filters you wish to run on them. Then, you run a video
application, such as VirtualDub, and open the script file. This is when
AviSynth takes action. It opens the videos you referenced in the script, runs
the specified filters, and feeds the output to video application. The
application, however, is not aware that AviSynth is working in the
background. Instead, the application thinks that it is directly opening a
filtered AVI file that resides on your hard drive.

There is much new and re-discovered functionality in AviSynth2. To make those
items clearly visible (especially when the feature was not well documented in
the past) they are marked with **v2**

The version 2.5 is a major internal upgrade. Read `AviSynth 2.5`_ carefully
before you use it. Relevant changes are marked with **v2.5**
Linear Editing:
:::::::::::::::

The simplest thing you can do with AviSynth is the sort of editing you can do
in VirtualDub. The scripts for this are easy to write because you don't have
to worry about variables and complicated expressions if you don't want.

For testing create a file called test.avs and put the following single line
of text in it: ::Version

Now open this file with e.g. Windows Media Player and you should see a ten-
second video clip showing AviSynth's version number and a copyright notice.

``Version`` is what's called a "source filter", meaning that it generates a
clip instead of modifying one. The first command in an AviSynth script will
always be a source filter.

Now add a second line to the script file, so that it reads like this:
  ::Version
    ReduceBy2

Reopen the file in Media Player. You should see the copyright notice again,
but now half as large as before.
```ReduceBy2`_`` is a "transformation filter," meaning that it takes the
previous clip and modifies it in some way. You can chain together lots of
transformation filters, just as in VirtualDub.
Let's add another one to make the video fade to black at the end. Add another
line to the script file so that it reads: ::Version
    ReduceBy2
    FadeOut(10)

Now reopen the file. The clip should be the same for the first 9 seconds, and
then in the last second it should fade smoothly to black.
The `FadeOut`_ filter takes a numerical argument, which indicates the number
of frames to fade.

It takes a long time before the fade starts, so let's trim the beginning of
the clip to reduce the wait, and fade out after that.
Let's discard the first 120 of them, and keep the frames 120-150:
  ::Version
    ReduceBy2
    # Chop off the first 119 frames, and keep the frames 120-150
    # (AviSynth starts numbering frames from 0)
    Trim(120,150)
    FadeOut(10)

In this example we used a comment for the first time.
Comments start with the # character and continue to the end of the line, and
are ignored completely by AviSynth.
The `Trim`_ filter takes two arguments, separated by a comma: the first and
the last frame to keep from the clip. If you put 0 for the last frame, it's
the same as "end of clip," so if you only want to remove the first 119 frames
you should use Trim(120,0).

Keeping track of frame numbers this way is a chore. It's much easier to open
a partially-completed script in an application like VirtualDub which will
display the frame numbers for you. You can also use the ` ShowFrameNumber`_
filter, which prints each frame's number onto the frame itself.

In practice a much more useful source filter than `Version`_ is `AVISource`_,
which reads in an AVI file (or one of several other types of files) from
disk. If you have an AVI file handy, you can try applying these same filters
to your file:
  ::AVISource("d:\capture.avi")  # or whatever the actual pathname is
    ReduceBy2
    FadeOut(15)
    Trim(120,0)

Even a single-line script containing only the AVISource command can be useful
for adding support for >2GB AVI files to applications which only support <2GB
ones.


--------


Non-Linear Editing:
:::::::::::::::::::

Now we're getting to the fun part. Make an AVS file with the following script
in it: ::StackVertical(Version, Version)

Now open it. Result: An output video with two identical lines of version
information, one on top of the other.
Instead of taking numbers or strings as arguments, `StackVertical`_ takes
video clips as arguments. In this script, the Version filter is being called
twice. Each time, it returns a copy of the version clip. These two clips are
then given to `StackVertical`_, which joins them together (without knowing
where they came from).

One of the most useful filters of this type is `UnalignedSplice`_, which
joins video clips end-to-end. Here's a script which loads three AVI files
(such as might be produced by AVI_IO) and concatenates them together.
::UnalignedSplice(AVISource("d:\capture.00.avi"), \
      AVISource("d:\capture.01.avi"), \
      AVISource("d:\capture.02.avi"))

Both `StackVertical`_ and `UnalignedSplice`_ can take as few as two arguments
or as many as sixty.
You can use the ``+`` operator as a shorthand for `UnalignedSplice`_.

For example, this script does the same thing as the previous example:
::AVISource("d:\capture.00.avi") + \
      AVISource("d:\capture.01.avi") + \
      AVISource("d:\capture.02.avi")

Now let's suppose you're capturing with an application that also saves the
video in multiple AVI segments, but puts the audio in a separate WAV file.
Can we recombine everything? You bet:
::AudioDub(AVISource("d:\capture.00.avi") + \
      AVISource("d:\capture.01.avi") + \
      AVISource("d:\capture.02.avi"), \
      WAVSource("d:\audio.wav"))

--------


Syntax
-------


Expressions:
::::::::::::

An AviSynth script consists of multiple lines of statements looking like
this:   ::variable_name = expression

In this example expression is evaluated and the result is assigned to
variable_name.

Very important is the common shortcut form: ::expression

In this case, expression is evaluated and the result is assigned to the
special clip variable last.
This is the same as ::last = expression

The end of the script often looks like: ::return expression

Here expression is evaluated and is used as the "return value" of the script
--that is, the video clip that will be seen by the application which opens
the AVS file.

If "return" is not specified explicitly, the clip last is used as a "return
value".

The basic form of an expression which invokes a function is ::Function(args)

Clip functions always produce a new video clip and never modify an existing
one,
Args is a list of function arguments separated by commas. The list can be
empty (which means all or some arguments can be optional)

If the filter function expects a video clip as its first argument, and that
argument is not supplied, then the clip in the special variable last will be
used.

AviSynth filters can take named arguments. The named arguments can be
specified in any order,
and the filter will choose default values for any that you leave off (named
arguments are always optional).
This makes certain filters much easier to use. ::You can write

    Subtitle("Hello, World!", text_color=$00FF00, x=100, y=200)

    instead of

    Subtitle("Hello, World!", 100, 200, 0, 999999, "Arial", 24, $00FF00)

An alternate syntax (called "OOP notation") for clip functions is
::expression.Function(args)

    e.g.:
    Version.ReduceBy2.FadeOut(15)

This is equivalent to ::Function(expression, args)

    e.g.:
    FadeOut(15, ReduceBy2(Version))

and can be thought of ``Function`` applied to ``expression``.
One disadvantage of OOP notation is that it can only be used with filters
which take a single video-clip argument, not with filters which take several.

All AviSynth functions produce defined number of output frames and framerate,
even if the statement seems very complex.
AviSynth knows after having read the script how long the output will be,
which framerate it has and the "cutting sequence" of all used inputs
This is all calculated on opening the script. Only the actual filtering is
done runtime on request.


--------

**Comments**: AviSynth ignores anything from a # character to the end of that
line: ::# comment

In *v2.58* it is possible to add block and nested block comments in the
following way: ::# block comment:
    /*
    comment 1
    comment 2
    */ ::# nested block comments:
    [* [* a meaningful example with follow later :) *] *]

AviSynth ignores anything from an ``__END__`` keyword (with double
underscores) to the end of the script file. This can be used to disable some
last commands of script.

::Version()
    __END__
    ReduceBy2()
    Result is not reduced and we can write any text here


**Ignore Case**: aViSouRCe is just as good as AVISource.

**Continue** on next or from previous line: \ ::Subtitle ("Test-Text")

    Subtitle ( \
              "Test-Text")

    Subtitle (
           \ "Test-Text")

--------


Variables:
::::::::::

A variable name can be up to 50 characters long (actually more than 4000
characters in Avisynth *v2.56*) and can contain (English) letters, digits,
and underscores (_), but no other characters. The name cannot start with a
digit.

You may use characters from your language system codepage (locale) in strings
and file names (ANSI 8 bit only, not Unicode).

The following types of variables can be used:

clip: a video clip containing video and / or audio. At least one variable for
a clip must be used and returned by the script.
string: surrounded either by "quotation marks" or by 3 quotation marks like
"""this example""". A text string can contain any character except the
terminating quotation mark or double-apostrophe. If you need to put a
quotation mark inside a string, use the triple quote-notation: ::Subtitle
("""This displays "hello world" with quotes""")

int: entered as a string of digits, optionally with a + or - at the
beginning.
float: entered as a string of digits with a period (.) somewhere in it and an
optional + or -. For example, +1. is treated as a floating-point number.
val: as type of a function argument where it does not matter if it is int or
float
bool: can be TRUE or FALSE
hexadecimal numbers: entered by preceding it with a $. This variable is
treated as an integer. Several filters use this notation for specifying
colors. For example, $FF8800 is a shade of orange.

global: defines a global variable, which can be used by all user-defined
functions and the main script in common.

Here's another version of the example from above that's more manageable and
easier to understand: ::a = AVISource("d:\capture.00.avi")
    b = AVISource("d:\capture.01.avi")
    c = AVISource("d:\capture.02.avi")
    sound_track = WAVSource("d:\audio.wav")

    AudioDub(a+b+c, sound_track)

--------


Colors
------

In some filters (BlankClip, Letterbox, AddBorders and FadeXXX) a color
argument can be specified. In all cases the color should be specified in RGB
format even if the color format of the input clip is YUV. This can be done in
hexadecimal or decimal notation. In hexadecimal notation the number is
composed as follows: the first two digits denote the red channel, the next
two the green channel and the last two the blue channel. The hexadecimal
number must be preceded with a $. In decimal notation the number is as
follows: the red channel value is multiplied by 65536, the green channel
value is multiplied by 256 and the two resulting products are both added to
the blue channel value.

Let's consider an example. Brown is given by R=$A5 (165), G=$2A (42), B=$2A
(42). Thus ``BlankClip(color=$A52A2A)`` gives a brown frame. Converting each
channel to decimal (remember that A=10, B=11, C=12, D=14, E=14, F=15) gives
::R = $A5 = 10*16^1 +  5*16^0 = 165
    G = $2A =  2*16^1 + 10*16^0 =  42
    B = $2A =  2*16^1 + 10*16^0 =  42

    165*65536 + 42*256 + 42 = 10824234

Thus creating a brown frame specifying the color in decimal notation gives
``BlankClip(color=10824234)``.

Common color presets can be found in the file colors_rgb.avsi, which should
be present in your plugin autoload folder (look into the file for list of
presets). Thus ``BlankClip(color=color_brown)`` gives the same brown frames.

Note that black RGB=$000000 will be converted to Y=16, U=V=128 if the
colorformat of the input clip is YUV, since the default color conversion RGB
[0,255] -> YUV [16,235] is used.

--------


Operators
----------

For all types of operands (clip, int, float, string, bool) you can use:
``==`` is equal to
``!=`` is not equal to

For numeric types (int, float):
``+ ``add
``- ``subtract
``* ``multiply
``/ ``divide
``% ``mod
``>=`` greater than or equal to
``<=`` less than or equal to
``< ``less than
``> ``greater than

AviSynth in former versions parsed expressions from right to left, which gave
unexpected results: ::a = 10 - 5 - 5
    resulted in 10 - (5 - 5) = 10
    instead of (10 - 5) - 5 = 0 ! This bug has been corrected! Starting
    from v2.53 also multiplication and division are parsed from left to right
    (instead of right to left).

For string type:
``+ ``add
``>=`` greater or equal than (case-insensitive)
``<=`` less or equal than (case-insensitive)
``< ``less than (case-insensitive)
``> ``greater than (case-insensitive)

For clip type:
``+ ``the same as the function ``UnalignedSplice``
``++`` the same as the function ``AlignedSplice``

For bool type (true/false):
``||`` or
``&&`` and
``?:`` execute code conditionally ::b = (a==true) ? 1 : 2

    This means in pseudo-basic:

    if (a=true) then b=1 else b=2

--------


Script Functions
-----------------

The input and output of these functions are not clips, but some other
variables used in the script.
Numerical functions:
::::::::::::::::::::

``Max(int, int[, ...])`` / ``Max(float, float[, ...])``: Maximum value of a
set of numbers. ``Max`` (1, 2) = 2
``Max`` (5, 3.0, 2) = 5.0
``Min(int, int[, ...])`` / ``Min(float, float[, ...])``: Minimum value of a
set of numbers. ``Min`` (1, 2) = 1
``Min`` (5, 3.0, 2) = 2.0
``MulDiv(int, int, int)``: (m*n+d/2)/d using 64 bit intermediate result
``MulDiv`` (1, 1, 2) = 1
``MulDiv`` (2, 3, 2) = 3
``Floor(float)``: converts from float to int ``Floor`` (1.2) = 1
``Floor`` (1.6) = 1
``Floor`` (-1.2) = -2
``Floor`` (-1.6) = -2
``Ceil`` (float): converts from float to int ``Ceil`` (1.2) = 2.0
``Ceil`` (1.6) = 2.0
``Ceil`` (-1.2) = -1
``Ceil`` (-1.6) = -1
``Round`` (float): converts from float to int ``Round`` (1.2) = 1
``Round`` (1.6) = 2
``Round`` (-1.2) = -1
``Round`` (-1.6) = -2
``Int`` (float): Converts from float to int (round towards zero). ``Int``
(1.2) = 1
``Int`` (1.6) = 1
``Int`` (-1.2) = -1
``Int`` (-1.6) = -1
``Float`` (int): Converts int to float. ``Float`` (1) = 1.0
``Frac`` (float): Returns the fractional portion of the value provided.
``Frac`` (3.7) = 0.7
``Frac`` (-1.8) = -0.8
``Abs`` (integer) / ``Abs`` (float): Returns the absolute value (returns
float for float, integer for integer). ``Abs`` (-6) = 6
``Abs`` (-1.8) = 1.8
``Sign`` (int) / ``Sign`` (float): Returns sign of value (1, 0 or -1).
``Sign``(-3.5) = -1
``Sign``(3.5) = 1
``Sign``(0) = 0
``HexValue`` (string) Evaluates string as hexadecimal value. ``HexValue``
("FF00") = 65280
``Sin`` (float) Returns the sine of the argument (assumes it is radians).
Sin(Pi()/4) = 0.707
Sin(Pi()/2) = 1.0
``Cos`` (float) Returns the cosine of the argument (assumes it is radians).
Cos(Pi()/4) = 0.707
Cos(Pi()/2) = 0.0
``Pi`` () Returns the value of the "pi" constant (the ratio of a circle's
perimeter to its diameter). d = Pi() # d == 3.141593
``Log`` (float) Returns the natural (base-e) logarithm of the argument.
Log(1) = 0.0
Log(10) = 2.30259
``Exp`` (float) Returns the natural (base-e) exponent of the argument. Exp(1)
= 2.718282
Exp(0) = 1.0
``Pow`` (float base, float power) Returns "base" raised to the power
indicated by the second argument. Pow(2, 3) = 8
Pow(3, 2) = 9
Pow(3.45, 1.75) = 8.7334
``Sqrt`` (float) Returns the square root of the argument. Sqrt(1) = 1.0
Sqrt(2) = 1.4142
``Rand`` ([int max] [, bool scale] [, bool seed]): returns random integer
between 0 and max.
  defaults: max = 32768,  scale = TRUE,  seed = FALSE
  Scale = FALSE, modulus mode, (Rand(32768)%limit)
  Seed = TRUE, use time as seed ``Rand``(100) = integer number between 0
  and 99, all number equally probable.
``Rand``(32767, False) = integer number between 0 and 32766, with 0 two times
more probable than the other numbers.
``Spline`` (float X,  x1,y1, x2,y2, ...., bool "cubic"}** v2.5**
 Interpolates the Y value at point X using the control points x1/y1,...
 There have to be at least 2 x/y-pairs.
 The interpolation can be cubic (the result is a spline) or linear (the
 result is a polygon) ``Spline`` (5, 0,0, 10,10, 20,0, false) = 5
``Spline`` (5, 0,0, 10,10, 20,0, true) = 7

String functions:
:::::::::::::::::

``UCase`` (string): returns the string in uppercase ``UCase`` ("AviSynth") =
"AVISYNTH"
``LCase`` (string): returns the string in lowercase ``LCase`` ("AviSynth") =
"avisynth"
``RevStr`` (string): returns the string in reverse ``RevStr`` ("AviSynth") =
"htnySivA"
``StrLen`` (string): returns the length of string ``StrLen`` ("AviSynth") = 8
``Findstr`` (string1, string2):
returns the offset of string2 inside string1. The search is case-sensitive.
``Findstr`` ("AviSynth","syn") = 4
``LeftStr`` (string, length) / ``RightStr`` (string, length):
returns left or right portion of string specified by length ``LeftStr``
("AviSynth",3) = "Avi"
``MidStr`` (string, start [, length]):
returns portion of string starting at start (for the first character start=1)
for the number of characters specified by length or to the end. ``MidStr``
("AviSynth",3,2) = "iS"
``Chr`` (int): returns the ASCII character **v2.5** ``Chr`` (34) returns the
quote character
``Time`` (string): returns a string with the current system time formatted as
defined by the string **v2.5**
Codes for output formatting:
%a Abbreviated weekday name
%A Full weekday name
%b Abbreviated month name
%B Full month name
%c Date and time representation appropriate for locale
%d Day of month as decimal number (01 - 31)
%H Hour in 24-hour format (00 - 23)
%I Hour in 12-hour format (01 - 12)
%j Day of year as decimal number (001 - 366)
%m Month as decimal number (01 - 12)
%M Minute as decimal number (00 - 59)
%p Current locale's A.M./P.M. indicator for 12-hour clock
%S Second as decimal number (00 - 59)
%U Week of year as decimal number, with Sunday as first day of week (00 - 53)
%w Weekday as decimal number (0 - 6; Sunday is 0)
%W Week of year as decimal number, with Monday as first day of week (00 - 53)
%x Date representation for current locale
%X Time representation for current locale
%y Year without century, as decimal number (00 - 99)
%YYear with century, as decimal number
%z, %Z Time-zone name or abbreviation; no characters if time zone is unknown
%% Percent sign

The # flag may prefix any formatting code. In that case, the meaning of the
format code is changed as follows.

%#a, %#A, %#b, %#B, %#p, %#X, %#z, %#Z, %#% # flag is ignored.
%#c Long date and time representation, appropriate for current locale. For
example: "Tuesday, March 14, 1995, 12:41:29".
%#x Long date representation, appropriate to current locale. For example:
"Tuesday, March 14, 1995".
%#d, %#H, %#I, %#j, %#m, %#M, %#S, %#U, %#w, %#W, %#y, %#Y Remove leading
zeros (if any).

Conversions:
::::::::::::

``Value`` (string): Returns the value of an string. ``Value`` ( "-2.7" ) =
-2.7
``String`` (float / int / string, format_string): converts a number to a
string.


If the variable is float or integer, it converts it to a float and uses the
format_string to convert it to a string.

The syntax of the format_string is as follows:

%[flags][width][.precision]f
width: the minimum width (the string is never truncated)
precision: the number of digits printed
flags:
`` -   ``left align (instead right align)
`` +   ``always print the +/- sign
`` 0   ``padding with leading zeros
`` ' ' ``print a blank instead of a "+"
`` #   ``always print the decimal point

e.g. ``Subtitle`` ("Clip height is " + ``String`` (last.height) )

``String``(1.23, "%f") = '1.23'
``String``(1.23, "%5.1f") = ' 1.2'
``String``(1.23, "%1.3f") = '1.230'

Version checking functions:
:::::::::::::::::::::::::::

``VersionNumber`` ()
Returns AviSynth version number as float ``VersionNumber`` () = 2.56
``VersionString`` ()
Returns AviSynth version info as string (first line used in ``Version``
command). ``VersionString`` () = "AviSynth 2.56, build:Oct 28 2005
[18:43:54]"

Test functions:
:::::::::::::::

``IsBool(var) ``
``IsInt(var) ``
``IsFloat(var) ``
``IsString(var) ``
``IsClip(var) ``
Other functions:
::::::::::::::::

``Select`` (index, item0 [, item1...]): Returns item selected by the index
(0=item0). Items can be any variable or clip and can even be mixed.
``Defined`` (var): for defining optional parameters in user-defined
functions.
``Default`` (x, d): returns x if Defined(x), d otherwise.
``Exist`` (filename): returns TRUE or FALSE after checking if the file
exists.
``NOP`` (): returns NULL, provided mainly for conditional execution with non-
return value items such as import and no "else" condition desired.
``Eval`` (string),
``Apply`` (func-string, arg,...): ``Eval`` ("f(x)") is equivalent to ``f(x)``
is equivalent to ``Apply`` ("f", x) ::You can use Eval for something like:
    settings = "352, 288"
    Eval( "BicubicResize(" + settings + ")" )

``Import``(filename): evals contents of another AviSynth script (imports the
text of another script)

For error reporting and catching bad input to user-defined function you can
use:
``Assert``(bool, string error-message)

``Try ... Catch``: this is a function for checking if an error WILL arise:
::Try {
      AviSource("file.avi")
    }
    Catch(err_msg) {
       Blackness.Subtitle(err_msg)
    }

--------


Runtime Functions
-----------------

There are now `Conditional Filters`_ which evaluate scripts when a frame is
processed, so you can change variables on a per-frame basis.
To have more applications there have to be `Runtime Functions`_ which
evaluate the content of the clip and return a value. **v2.5**

A simple example is to calculate the average luma for each frame and display
it. ::Version()      # Generate a test clip
    ConvertToYV12()# We need YV12
    FadeIn(10)     # Make the luma variable so
                   # we can see something happen

                   # Evaluate Subtitle(...) for each frame
                   # the output of AverageLuma is
                   converted to
                   # a string and Subtitled on the input
                   clip
    ScriptClip(" Subtitle(String(AverageLuma())) ")
    ConvertToRgb   # View it in RGB

--------


Control Functions
------------------

``SetMemoryMax`` (int): Sets the maximum memory that AviSynth uses (in MB).
Setting to zero just returns the current Memory Max value.** v2, (=0)
v2.5.8**

In the 2.5 series the default Memory Max value is 25% the free physical
memory, with a minimum of 16MB. From rev 2.5.8 RC4, the default Memory Max is
also limited to 512MB.

Free memory: <64 128 256 512 1024 2048 3072
Default Max v2.5.7 and older: 16 32 64 128 256 512 768
Default Max since v2.5.8 RC4: 16 32 64 128 256 512 512

In some older versions there is a default setting of 5MB, which is quite low.
If you encounter problems (e.g. low speed) try to set this values to at least
32MB. Too high values can result in crashes because of 2GB address space
limit. Return value: Actual MemoryMax value set.

``SetPlanarLegacyAlignment`` (clip, bool): Set alignment mode for planar
frames. **v2.5.6**

Some older plugins illegally assume the layout of video frames in memory.
This special filter forces the memory layout of planar frames to be
compatible with prior version of AviSynth. The filter works on the GetFrame()
call stack, so it effects filters **before** it in the script.

::**Example : Using an older version of Mpeg2Source()**

    LoadPlugin("...\Mpeg2Decode.dll")
    Mpeg2Source("test.d2v")         # A plugin that illegally
                                    #
                                    assumes the layout of memory
    SetPlanarLegacyAlignment(true)  # Set legacy memory alignment
                                    # for
                                    prior statements
    ConvertToYUY2()                 # Statements thru to the end
                                    # of
                                    the script have advanced
    ...                             # memory alignment.

``SetWorkingDir`` (string): Sets the default directory for Avisynth. **v2**

This is primarily for easy loading of source clips, etc. Does not affect
plugin autoloading. Return value: 0 if successful, -1 otherwise.

``global OPT_AllowFloatAudio=True``: **v2.57**
This option enables WAVE_FORMAT_IEEE_FLOAT audio output. The default is to
autoconvert Float audio to 16 bit.

``global OPT_UseWaveExtensible=True``: **v2.58**
This option enables WAVE_FORMAT_EXTENSIBLE audio output. The default is
WAVE_FORMAT_EX.

Note: The default DirectShow component for .AVS files, "AVI/WAV File Source",
does not correctly implement WAVE_FORMAT_EXTENSIBLE processing, so many
application may not be able to detect the audio track. There are third party
DirectShow readers that do work correctly. Intermediate work files written
using the AVIFile interface for later DirectShow processing will work
correctly if they use the DirectShow "File Source (async)" component or
equivalent.

--------


Clip Properties
---------------

These functions take a clip as input and you get back a property of the clip.
``Width`` (clip) Returns the width of the clip in pixels (type: int).
``Height`` (clip) Returns the height of the clip in pixels (type: int).
``Framecount`` (clip) Returns the number of frames of the clip (type: int).
``Framerate`` (clip) Returns the number of frames per seconds of the clip
(type: float).
``FramerateNumerator`` (clip) **v2.55**
``FramerateDenominator`` (clip) **v2.55**
``Audiorate`` (clip) Returns the sample rate of the audio of the clip.
``Audiolength`` (clip) Returns the number of samples of the audio of the clip
(type: int). Be aware of possible overflow on very long clips ( 2^31 samples
limit).
``AudiolengthF`` (clip) **v2.55** Returns the number of samples of the audio
of the clip (type: float).
``Audiochannels`` (clip) Returns the number of audio channels of the clip.
``Audiobits`` (clip) Returns the audio bit depth of the clip.
``IsAudioFloat`` (clip) **v2.55** Returns true if the bit depth of the audio
of the clip is float.
``IsAudioInt`` (clip) **v2.55** Returns true if the bit depth of the audio of
the clip an integer.
``IsRGB`` (clip) Returns true if the clip is RGB, false otherwise (type:
bool).
``IsRGB24`` (clip) Returns true if the clip is RGB24, false otherwise (type:
bool).
``IsRGB32`` (clip) Returns true if the clip is RGB32, false otherwise (type:
bool).
``IsYUY2`` (clip) Returns true if the clip is YUY2, false otherwise (type:
bool).
``IsYV12`` (clip) **v2.51** Returns true if the clip is YV12, false otherwise
(type: bool).
``IsYUV`` (clip) **v2.54** Returns true if the clip is YUV, false otherwise
(type: bool).
``IsPlanar`` (clip) **v2.51** Returns true if the clip color format is
planar, false otherwise (type: bool).
``IsInterleaved`` (clip) **v2.51** Returns true if the clip color format is
interleaved, false otherwise (type: bool).
``IsFieldBased`` (clip)
``IsFrameBased`` (clip)
``GetParity`` (clip, int "n") Returns true if frame n (default 0) is top
field of fieldbased clip, or it is full frame with top field first of
framebased clip (type: bool).
``HasAudio`` (clip) **v2.56** Returns true if the clip has audio, false
otherwise (type: bool).
``HasVideo`` (clip) **v2.56** Returns true if the clip has video, false
otherwise (type: bool).

Don't forget: you can use the Properties with the implicit variable LAST or
in OOP-notation: ::BilinearResize(Width/2, Height/2)
       is the same as
    BilinearResize(Width(Last)/2, Height(Last)/2)
       is the same as
    BilinearResize(Last.Width / 2, Last.Height / 2)

--------


User-Defined Functions
-----------------------

You can define your own functions. This is best explained by an example:
  ::Function NTSC2PAL( clip c) {
        Assert(c.height == 480, \
               "NTSC2PAL: input clip must have 480 scan
               lines")
        Bob(c, height=576)
        return Weave()
    }

Even recursive functions can be defined.
  ::function TRANSITION(clip clip, int start, int expo, int overlap)
    {
       return ( start >= clip.framecount-expo ?
    \      Trim(clip,start,0) :
    \      Dissolve(Trim(clip,start,start+expo-1),
    \         TRANSITION(clip,start+expo,expo,overlap),
    \         overlap
    \              )
    \         )
    }

--------


Functions with more than one input clip
----------------------------------------

There are some functions which combine two or more clips in different ways.
How the video content is calculated is described for each function, but here
is a summary which properties the result clip will have.

The input clips must always have the same color format and - with the
exception of *Layer* - the same dimensions.
**frame-rate** **frame-count** **audio content** **audio sampling rate**
**AlignedSplice, UnalignedSplice** first clip  sum of all clips  see filter
description  first clip
**Dissolve** sum of all clips minus the overlap  see filter description
**Merge, MergeLuma, MergeChroma, Merge(A)RGB** first clip  the last frame
of the shorter clip
is repeated until
the end of the clip  first clip
**Layer**
**Subtract** longer clip
**StackHorizontal, StackVertical**
**Interleave** (fps of first clip)
x
(number of clips)  N x frame-count of longer clip

As you can see the functions are not completely symmetric but take some
attributes from the FIRST clip.


--------


Plugins
--------

With these functions you can add external functions to AviSynth.

``LoadPlugin`` ("filename" [, ...])

Loads one or more external avisynth plugins (DLLs).


--------

``LoadVirtualDubPlugin`` ("filename", "filtername", preroll)

This loads a plugin written for VirtualDub. "filename" is the name of the
.vdf file. After calling this function, the filter will be known as
"filtername" in avisynth. VirtualDub filters only supports RGB32. If the
video happens to be in RGB24-format, then you must use ``ConvertToRGB32``
(``ConvertToRGB`` won't suffice).

Some filters output depends on previous frames; for those preroll should be
set to at least the number of frames the filter needs to pre-process to fill
its buffers and/or updates its internal variables.


--------

``LoadVFAPIPlugin`` ("filename", "filtername")

This allows you to use VFAPI plugins (TMPGEnc import plugins).


--------

``LoadCPlugin`` ("filename" [, ...])
``Load_Stdcall_Plugin`` ("filename" [, ...])

Loads so called Avisynth C-plugins (DLLs).
Load_Stdcall_Plugin() is an alias for LoadCPlugin().
C-plugins are created on pure C language and use special "AviSynth C API"
(unlike ordinary Avisynt plugins which are created with MS C++). C-plugins
must be loaded with LoadCPlugin() or Load_Stdcall_Plugin().

Kevin provides a LoadCPlugin.dll that overloads the LoadCPlugin() verb to
support plugins compiled using the C subroutine calling sequence, use
Load_Stdcall_Plugin() to load stdcall calling sequence plugins when using
Kevins version. Advice: keep these plugins outside your auto plugin loading
directory to prevent crashes. [`discussion`_] [`AVISynth C API (by
kevina20723)`_]

--------


Plugin autoload and name precedence **v2**
--

It is possible to put all plugins and script files with user-defined
functions or (global) variables in a directory from where all files with the
extension .AVSI (**v2.08, v2.5**, the type was .AVS in **v2.05-2.07**) and
.DLL are loaded at startup, unloaded and then loaded dynamically as the
script needs them.

.AVSI scripts in this directory should only contain function definitions and
global variables, no main processing section (else strange errors may occur),
it also is not recommended to put other files in that directory.

The directory is stored in the registry (the registry key has changed for
**v2.5**). You can use double-clicking a .REG-file with the following lines
to set the path (of course inserting your actual path):
  ::REGEDIT4


    [HKEY_LOCAL_MACHINE\SOFTWARE\Avisynth]
    "plugindir2_5"="c:\\program files\\avisynth 2.5\\plugins"

The order in which function names take precedence is as follows: ::user-
defined function (always have the highest priority)
       plugin-function (have higher priority than built-in
       functions, they will override a built-in function)
          built-in function

Inside those groups the function loaded at last takes precedence, there is no
error in a namespace conflict.


Plugin autoload and conflicting function names **v2.55**
-

Starting from v2.55 there is DLLName_function() support. The problem is that
two plugins can have different functions which are named the same. To call
the needed one, DLLName_function() support is added. It auto-generates the
additional names both for auto-loaded plugins and for plugins loaded with
LoadPlugin.

**Some examples:**

::# using fielddeinterlace from decomb510.dll
    AviSource("D:\captures\jewel.avi")
    decomb510_fielddeinterlace(blend=false)

Suppose you have  the plugins mpeg2dec.dll and mpeg2dec3.dll in your auto
plugin dir, and you want to load a d2v file with mpeg2dec.dll (which outputs
YUY2):

::# using mpeg2source from mpeg2dec.dll
    mpeg2dec_mpeg2source("F:\From_hell\from_hell.d2v")

or with mpeg2dec3.dll (which outputs YV12):

::# using mpeg2source from mpeg2dec3.dll
    mpeg2dec3_mpeg2source("F:\From_hell\from_hell.d2v")

$Date: 2008/12/06 16:37:26 $

.. _AviSynth 2.5: twopointfive.htm
.. _ReduceBy2: corefilters/reduceby2.htm
.. _FadeOut: corefilters/fade.htm
.. _Trim: corefilters/trim.htm
.. _ ShowFrameNumber: corefilters/showframes.htm
.. _Version: corefilters/version.htm
.. _AVISource: corefilters/avisource.htm
.. _StackVertical: corefilters/stack.htm
.. _UnalignedSplice: corefilters/splice.htm
.. _Conditional    Filters: corefilters/conditionalfilter.htm
.. _Runtime Functions: corefilters/conditionalfilter.htm#RuntimeFunctions
.. _discussion: http://forum.doom9.org/showthread.php?s=&threadid=58840
.. _AVISynth C API (by kevina20723):
    http://kevin.atkinson.dhs.org/avisynth_c/
