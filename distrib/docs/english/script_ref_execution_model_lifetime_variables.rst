
The script execution model - Scope and lifetime of variables
------------------------------------------------------------

There are essentially two scope types in the AviSynth script language:


Contents
--------

-   `1`_ ` Global scope`_
-   `2 Local scope`_
-   `3 Lifetime of variables`_
-   `4 A variables scope and lifetime example`_
-   `5 Code-injecting language facilities and scopes`_

    -   `5.1 Import and Eval`_
    -   `5.2 Runtime scripts`_
    -   `5.3 The try...catch block`_


Global scope
~~~~~~~~~~~~

Every `variable`_ placed in this scope can be freely accessed from any nested
block of script code at any level of nesting. That is, you can access a
global from the top-level script block, from inside a user `function`_ at any
level of recursion, as well as from inside `runtime scripts`_.

**Note:** One important precondition for the above rule to apply is that *you
must not have a local variable with the same name as a global one*. If you
define a local variable with the same name as a global one, then you can no
longer get (read) the value of the global variable in that specific local
scope. This is because AviSynth when given a variable's name it first
searches in the current local scope; only if the search fails the global
scope is searched. You can however set (write) the global's value, since in
that case the use of the keyword ``global`` distinguishes between a global
and a local variable.


Local scope
~~~~~~~~~~~

Variables placed in this scope can be accessed (read or written) *only* from
script code within that scope. This allows the isolation of nested local
scopes and makes the creation and usage of script functions possible.

The most important local scope is the top-level script scope (the one that is
created just before the executing script is parsed and evaluated). All non-
global variables defined inside the script-level source code reside there.
All the other local scopes are created due to function calls and are nested
inside this one.

Nested local scopes result from function or filter calls (plugin writers can
create nested scopes through ``env->PushContext()`` and
``env->PopContext()``) and can be created at an arbitrary depth. For example,
a recursive user function such as the one below:

::function strfill(string s, int count) {
        return count > 0 ? s + strfill(s, count - 1) : ""
    }

will result during its evaluation in the creation and subsequent destruction
of eleven nested local scopes if called with a value ten for its ``count``
argument.


Lifetime of variables
~~~~~~~~~~~~~~~~~~~~~

The lifetime of variables defined at the global and top-level script (local)
scope spans from the time of the definition (that is the first statement that
assigns a value to them) to the end of frame serving and the unload of
``avisynth.dll``.

The lifetime of variables defined at nested local scopes spans from the time
of the definition in the nested local scope to the end of the nested local
scope's lifetime. Since nested local scopes result from function / filter
calls, the nested scope's lifetime is the lifetime of the function / filter
call.


A variables scope and lifetime example
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

To clarify the statements of the previous section, the following example
demonstrates the scope and lifetime of variables in a moderately complex
AviSynth script that also includes runtime scripts.

What the script does is to divide a clip (after some processing tweaks) in 4
equal-sized regions and evaluate the average luma of each region per frame.
If this is outside a range defined by two thresholds, the corresponding
region is turned to all black (if below) or white (if above) for that frame.

::function Quartile(clip c, int quartile) {
        `Assert`_(quartile >= 0 && quartile <= 3, "Invalid
        Quartile!")
        hw = `Int`_(c.`Width`_() / 2)
        hh = Int(c.`Height`_() / 2)
        return `Select`_(quartile, \
            `Crop`_(c, 0, 0, hw, hh), Crop(c, hw, 0, hw, hh), \
            Crop(c, 0, hh, hw, hh), Crop(c, hw, hh, hw, hh))
    }

    function bracket_luma(clip c, float th1, float th2) {
        Assert(0 <= th1 && th1 < th2 && th2 <= 255, "Invalid
        thresholds!")
        script =  "th1 = " + `String`_(th1) + Chr(13) + Chr(10) + \
            "th2 = " + String(th2) + """
            avl = `AverageLuma`_()
            return avl <= th1 ? last.`BlankClip`_() : (avl >= th2
            ? \
                last.BlankClip(color=color_white) : last)
            """
        return `ScriptClip`_(c, script)
    }

    clp = `AviSource`_("myclip.avi")
    clp = `Tweak`_(clp, hue=20, sat=1.1)
    threshold1 = 12.0
    threshold2 = 78.0
    q0 = Quartile(clp, 0).bracket_luma(threshold1, threshold2)
    q1 = Quartile(clp, 1).bracket_luma(threshold1, threshold2)
    q2 = Quartile(clp, 2).bracket_luma(threshold1, threshold2)
    q3 = Quartile(clp, 3).bracket_luma(threshold1, threshold2)
    `StackVertical`_(StackHorizontal(q0, q1), `StackHorizontal`_(q2, q3))

The scope and lifetime of all variables in the example script is presented in
the following timeline (the ``color_white`` global is from the autoloaded
.avsi that ships with AviSynth):

::+-- scope --+------- parsing phase ---------------------->+----- frame
serving phase ------->+
    |           |
    |
    | global    |color_white - - - - - - - - - - - - - - - - - - - - - -
    - - - - - - - - - - - ->|
    +-----------+---------------------------------------------+----------
    ------------------------|
    | local,    |clp - - - - - - - - - - - - - - - - - - - - - - - - - -
    - - - - - - - - - - - ->|
    | top-level | threshold1,threshold2- - - - - - - - - - - - - - - - -
    - - - - - - - - - - - ->|
    |           |  q0,q1,q2,q3 - - - - - - - - - - - - - - - - - - - - -
    - - - - - - - - - - - ->|
    |           |
    |avl,th1,th2 - - - - - - - - - - ->|
    +-----------+---------------------------------------------+----------
    ------------------------|
    | local,    |   c,  - - - ->|           |                |
    | Quartile  |   quartile, ->|           | repeated       |
    | function  |    hw,hh- - ->|           | three times,   |
    +-----------+-------------------------->| in immediate ->|
    | local,    |   |            c, - - - ->| succession     |
    | bracket_l.|   |            th1,th2, ->|                |
    | function  |   |             script- ->|                |
    +-----------+---------------------------------------------+----------
    ------------------------|
Code-injecting language facilities and scopes
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

There are certain language constructs (functions, filters and control
structures) that allow the injection of code in the script, ie the execution
of arbitrary sequences of AviSynth script language `statements`_.

This is a *very* useful functionality that allows among other things dynamic
code evaluation, the creation of `block statements`_ and `arrays`_, the
organisation of AviSynth code in libraries, etc. However, there are some
subtle issues regarding variables' scope and visibility that can lead to
surprises if not fully understood.


Import and Eval
:::::::::::::::

`Import`_() and `Eval`_() evaluate the passed-in script source code in the
context of the current local scope.

This means that variables contained in the top-level scope of the imported
script or in the code string passed to Eval() are created inside the current
local scope and become available for read/write to the following script
source code. For example:

**1. File "a.avs"**

::x = 12
    y = 24
    c = `BlankClip`_(pixel_type="YV12", color=color_orange, width=240,
    height=180)

**2. File "b.avs"**

::`Import`_("a.avs")
    `AviSource`_("myvideo.avi")
    `Levels`_(**x**, 1.0, 255, **y**, 242)
    `Overlay`_(**c**, x=last.Width-320, y=last.Height-240, mode="chroma")

In addition, the imported script or the code string passed to Eval() can use
previously defined in that scope local variables (as well as globals, of
course). For example (the use of multiline triply quoted strings makes easier
the writing of `block statements`_):

::x = 5
    AviSource("aclip.avi")
    f = `Framecount`_()
    f < 100 ? `Eval`_("""
        `Trim`_(x, f-2)
        x = 0
    """) : Eval("""
        Trim(x, 15*x + 30)
        x = 1
    """)
    x == 0 ? `Invert`_() : `Subtitle`_(String(last.Framecount))

Especially the later is something that you must always keep in mind -mostly
for `Import`_() since the code is not immediately visible; only the filename
shows up in the script- because it has the potential to introduce bugs by
unexpected overriding of a variable's value.

Consider, the following example:

**1. File "mylib.avsi"**

::function preset(int num) { # 0 to 3
        return `Select`_(num, AviSource("..."), AviSource("..."),
        AviSource("..."), AviSource("..."))
    }
    global def_preset = preset(0)

**2. File "myscript.avs"**

::global def_preset = `AviSource`_("myfav.avi")
    Import("mylib.avsi")
    `Tweak`_(def_preset, hue=20) # oops, using clip from mylib.avsi
    instead of myscript.avs!
    ...

The imported script changed a previously defined variable and the results
will now be suprising (until of course the bug is discovered).

However, this same feature has a number of interesting possibilities, for
example:

-   You can define sub-scripts that communicate with the parent script
    through a defined set of variables.
-   You can create libraries (AviSynth include files) that perform
    initialisation code based on "environment" variables (the ones you set in
    the parent script before importing) and / or return status information
    (through a variable that they set at the global or top-script level code)
-   You can implement `block statements`_.

**Note:** To test for the existence of input/output variables in the above
scenarios try to read their value in a ``try..catch`` block; else your script
will die hard if for any reason they do not exist.


Runtime scripts
:::::::::::::::

Local variables inside runtime filters' scripts are **always** binded to the
top-level script local scope; even if the filter calls were made inside a
user function. This is because the parsing of runtime scripts is done *after*
the parsing of the script, at the frame serving phase. At that point in
script execution, nested local scopes have already vanished and only the
global and the top-level script local scopes survive.

The same is true for the `special variables`_ set by the runtime filters
(such as for example ``current_frame``); they are defined at the top-level
script local scope.

Some consequences of the above setup are the following:

-   You can use top-level script local variables inside the runtime
    scripts to pass information, just as is customary to do with global ones.
-   You must be careful if you define local variables in your runtime
    scripts to not clash with local variables in other runtime scripts in the
    filter chain. This is also true for globals, but globals are typically
    used for inter-filter communication; use of locals is not so common and
    thus may be overlooked by script writers.
-   Overriding a variable (either local or global) does not have an efect
    at the main script, because the evaluation of the main script is done at
    the parsing phase, before the execution of any runtime script.
-   When examining the way that a variable will be modified by a chain of
    runtime scripts, you must remember that the evaluation of scripts is done
    from bottom to top, just like the fetching of frames.

Consider the following example:

::`AviSource`_("myclip.avi")
    x = 5
    fc = `Framecount`_()
    fc > 2x ? `Trim`_(x, fc - x) : Trim(0, fc - x)
    fc = Framecount()
    `ScriptClip`_("""`Subtitle`_("and the value of x is : " +
    `String`_(x))""")
    `FrameEvaluate`_("x = (x % 3 == (fc - x - 1) % 3) ? x + 2 : x - 1")
    FrameEvaluate("x = current_frame")

The assignment ``x = 5`` at the main script is used to control trimming of
the source clip. ``x`` is passed as argument in the `Trim`_ filter during the
script's parsing phase. Thus the modifications by the runtime scripts that
start at the frame serving phase has no effect on the values passed to Trim.

By the time the first frame will be fetched, ``x`` will have been overrided
by the ``x = current_frame`` assignment in the last `FrameEvaluate`_ filter's
runtime script. Thus its value in the script has no effect (in this
particular case) to the results of the runtime filters processing.

Here, using ``x`` in all runtime filter scripts does not pose a naming clash
problem. ``x`` is the variable used to communicate state information along
the runtime filter chain. However, if we have needed a conditional assignment
by frame number and we have accidentally used the following runtime script in
place of the last FrameEvaluate line,

::FrameEvaluate("""
        fc = 12
        x = current_frame < fc ? current_frame : fc
        """)

then there would be a clash with the use of ``fc`` in the previous line (the
clips framecount would have been overwritten with an unrelated value) and the
logic of our processing would be in error.


The try...catch block
:::::::::::::::::::::

This may seem surprising at first, but the ``try...catch`` block does inject
code in the script (at the scope that contains it). If this code defines new
variables, then those variables are available to the code in the section that
follows the ``try...catch`` block. More specifically, there are two
possibilities:

-   *No error* occurs inside the ``try{...}`` section.

1.  All statements of the code contained in the ``try{...}`` section are
    evaluated and affect the script code that follows.

-   An error *does* occur inside the ``try{...}`` section.

1.  Statements of the code contained in the ``try{...}`` section up to
    the point of error are evaluated and affect the script code that follows.
2.  All statements of the code contained in the ``catch{...}`` section
    are evaluated and affect the script code that follows.
3.  The variable that is used the ``catch{...}`` section to store the
    error message becomes available to the script code that follows.

The following example code excerpt clarifies the above:

::a = ... # it is assumed that the (missing) code may result in a being
either 1 or 0
    try {
        y = 3
        x = 6 / a  # if a == 0 this will lead to an error
        z = 12
    }
    catch (msg) {
        NOP
    }
    ...code that follows...

Now, if ``a`` is *not* zero at the point the ``try...catch`` block is
evaluated, then three new local variables in the current scope will be
created (``x``, ``y`` and ``z``) and be available for use by the code that
follows.

If however, ``a`` *is* zero, then from the three variables in the try section
only ``y`` will be created; in addition, since the catch section will be
evaluated, ``msg`` will be created. Thus the variables available for use by
the code that follows will be ``x`` and ``msg``.

--------

Back to the `script execution model`_.

$Date: 2011/04/29 20:11:14 $

.. _1: #Global_scope
.. _Local scope: #Local_scope
.. _Lifetime of variables: #Lifetime_of_variables
.. _A variables scope and lifetime example:
    #A_variables_scope_and_lifetime_example
.. _Code-injecting language facilities and scopes: #Code-
    injecting_language_facilities_and_scopes
.. _Import and Eval: #Import_and_Eval
.. _Runtime scripts: #Runtime_scripts
.. _The try...catch block: #The_try...catch_block
.. _variable: syntax_script_variables.htm (Script variables)
.. _function: syntax_userdefined_scriptfunctions.htm (Script functions)
.. _runtime scripts: syntax_runtime_environment.htm (Runtime environment)
.. _Assert: syntax_internal_functions_control.htm (Internal
    functions/Control functions)
.. _Int: syntax_internal_functions_numeric.htm (Internal
    functions/Numeric functions)
.. _Width: syntax_clip_properties.htm (Clip properties)
.. _Crop: corefilters/crop.htm (Crop)
.. _String: syntax_internal_functions_conversion.htm (Internal
    functions/Conversion functions)
.. _AverageLuma: syntax_internal_functions_runtime.htm (Internal
    functions/Runtime functions)
.. _BlankClip: corefilters/blankclip.htm (BlankClip)
.. _ScriptClip: corefilters/conditionalfilter.htm (ScriptClip)
.. _AviSource: corefilters/avisource.htm (AviSource)
.. _Tweak: corefilters/tweak.htm (Tweak)
.. _StackVertical: corefilters/stack.htm (StackVertical)
.. _StackHorizontal: corefilters/stack.htm (StackHorizontal)
.. _statements: syntax_ref.htm (AviSynth Syntax)
.. _block statements: script_ref_block_statements.htm (Block statements)
.. _arrays: script_ref_arrays.htm (Arrays)
.. _Import: corefilters/import.htm (Import)
.. _Levels: corefilters/levels.htm (Levels)
.. _Overlay: corefilters/overlay.htm (Overlay)
.. _block statements: http://avisynth.org/mediawiki/Block_statements
    (Block statements)
.. _Trim: corefilters/trim.htm (Trim)
.. _Invert: corefilters/invert.htm (Invert)
.. _Subtitle: corefilters/subtitle.htm (Subtitle)
.. _Import: http://avisynth.org/mediawiki/Import (Import)
.. _Framecount: syntax_clip_properties.htm
.. _String: syntax_internal_functions_conversion.htm
.. _FrameEvaluate: corefilters/conditionalfilter.htm (FrameEvaluate)
.. _script execution model: script_ref_execution_model.htm (The script
    execution model)
