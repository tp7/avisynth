
AviSynth FAQ - General information
==================================


Contents
--------

1.  `What is AviSynth?`_
2.  `Who is developing AviSynth?`_
3.  `Where can I download the latest versions of AviSynth?`_
4.  `What are the main bugs in these versions?`_
5.  `Where can I find documentation about AviSynth?`_
6.  `How do I install/uninstall AviSynth?`_
7.  `What is the main difference between v1.0x, v2.0x, v2.5x, v2.6x and
    v3.x?`_
8.  `How do I know which version number of AviSynth I have?`_
9.  `How do I make an AVS-file?`_
10. `Where do I save my AVS-file?`_
11. `Are plugins compiled for v2.5x/v2.6x compatible with v1.0x/v2.0x and
    vice versa?`_
12. `How do I use a plugin compiled for v2.0x in v2.5x?`_
13. `How do I switch between different AviSynth versions without re-
    install?`_
14. `VirtualdubMod, WMP6.4, CCE and other programs crash every time on
    exit (when previewing an avs file)?`_
15. `My computer seems to crash at random during a second pass in any
    encoder?`_
16. `Is there a command line utility for encoding to DivX/XviD using
    AviSynth?`_
17. `Does AviSynth have a GUI (graphical user interface)?`_


What is AviSynth?
~~~~~~~~~~~~~~~~~

AviSynth (AVI SYNTHesizer) is a frameserver. An excellent description is
given on `Lukes homepage`_:

"AviSynth is a very useful utility created by Ben Rudiak-Gould. It provides
many options for joining and filtering videos. What makes AviSynth unique is
the fact that it is not a stand-alone program that produces output files.
Instead, AviSynth acts as the "middle man" between your videos and video
applications.

Basically, AviSynth works like this: First, you create a simple text document
with special commands, called a script. These commands make references to one
or more videos and the filters you wish to run on them. Then, you run a video
application, such as Virtualdub, and open the script file. This is when
AviSynth takes action. It opens the videos you referenced in the script, runs
the specified filters, and feeds the output to video application. The
application, however, is not aware that AviSynth is working in the
background. Instead, the application thinks that it is directly opening a
filtered AVI file that resides on your hard drive.

There are five main reasons why you would want to use AviSynth:

1.  Join Videos: AviSynth lets you join together any number of videos,
    including segmented AVIs. You can even selectively join certain portions
    of a video or dub soundtracks.
2.  Filter Videos: Many video processing filters are built in to
    AviSynth. For example, filters for resizing, cropping, and sharpening
    your videos.
3.  Break the 2 GB Barrier: AviSynth feeds a video to a program rather
    than letting the program directly open the video itself. Because of this,
    you can usually use AviSynth to open files larger than 2 GB in programs
    that don't natively support files of that size.
4.  Open Unsupported Formats: AviSynth can open almost any type of video,
    including MPEGs and certain Quicktime MOVs. However, when AviSynth feeds
    video to a program, it looks just like a standard AVI to that program.
    This allows you to open certain video formats in programs that normally
    wouldn't support them.
5.  Save Disk Space: AviSynth generates the video that it feeds to a
    program on the fly. Therefore, no temporary or intermediate videos are
    created. Because of this, you save disk space."


Who is developing AviSynth?
~~~~~~~~~~~~~~~~~~~~~~~~~~~

Originally AviSynth (up to v1.0b) was developed by Ben Rudiak-Gould. See
`mirror of his homepage`_. Currently it is developed by Sh0dan, IanB,
d'Oursse (AviSynth v3), Bidoche (AviSynth v3) and `others`_.


Where can I download the latest versions of AviSynth?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

The most recent stable version is v2.57, which can be found `here`_ (just as
more recent builds).


What are the main bugs in these versions?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Current bugs can be found in the documentation on the `AviSynth project
page`_. Fixed bugs can be found in the `Changelist`_.


Where can I find documentation about AviSynth?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Documentation about the filters of AviSynth can be found on this site `Main
Page`_, and in particular here: `Internal filters`_. You should read these
documents before posting to the forum, but it's OK to post if you have
trouble understanding them.


How do I install/uninstall AviSynth?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Starting from v2.06 AviSynth comes with an auto installer. Also make sure you
have no other versions of AviSynth floating around on your harddisk, because
there is a chance that one of those versions will be registered. Remove them
if necessary. For uninstalling AviSynth go to "program", "AviSynth 2.5" and
select "Uninstall AviSynth".

Installing AviSynth v2.05 or older versions: move avisynth.dll to your
system/system32 directory and run install.reg. For uninstalling run
uninstall.reg and delete avisynth.dll.


What is the main difference between v1.0x, v2.0x, v2.5x, v2.6x and v3.x?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

The versions v1.0x and v2.0x are compatible and outdated. The main difference
with v2.5x is that the internal structure of AviSynth has changed (YV12 and
multichannel support) with the consequence that external plugins compiled for
v1.0x/v2.0x will not work for v2.5x/v2.6x and vice versa. In v2.6x other
planar formats like YV24 and Y8 are added. v2.5x plugins will work in v2.6x
but not vice-versa. All versions are incompatible with v3.x, which will also
work under Linux/MacOSX (see `AviSynth v3`_) and rely on the GStreamer API.


How do I know which version number of AviSynth I have?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Open a text-editor, for example notepad. Add the following line

::Version()

and save the file with the extension "avs". Save for example as "version.avs"
(make sure that the extension is "avs" and not "txt"). Open the file in an
application which can read AVI-files, for example WMP 6.4 or Media Player
Classic. The version number will be displayed.


How do I make an AVS-file?
~~~~~~~~~~~~~~~~~~~~~~~~~~

Use your preferred text editor (e.g. Notepad). See also `this`_.

Although AviSynth doesn't need them, there are several GUIs (graphical user
interface) which may help you writing your AVS files. You can read a
description for each one of them `here`_.


Where do I save my AVS-file?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Anywhere on your hard-disk.


Are plugins compiled for v2.5x/v2.6x compatible with v1.0x/v2.0x and vice
versa?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
~~~

As explained `here`_ that is not the case. However it is possible to use a
v1.0x/v2.0x plugin in v2.5x/v2.6x, as explained `here`_.


How do I use a plugin compiled for v2.0x in v2.5x?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

In plugin collection `warpsharp_2003_1103.cab`_ you will find a plugin called
"LoadPluginEx.dll". (When using an older version of LoadPluginEx.dll, don't
move this plugin to your plugin dir. But move it to a separate folder,
otherwise VirtualdubMod and WMP6.4 will crash on exit.) This will enable you
using v2.0x plugins in v2.5x. An example script (using the v2.0x plugin Dust
by Steady):

::LoadPlugin("C:\Program Files\avisynth2_temp\plugins\LoadPluginEx.dll")
    LoadPlugin("C:\Program Files\avisynth2_temp\plugins\dustv5.dll")

    AviSource("D:\clip.avi")
    ConvertToYUY2()
    PixieDust(5)

If you want to automate this process, have a look at `LoadOldPlugins`_.


How do I switch between different AviSynth versions without re-install?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

-   You can use AvisynthSwitcher available `here`_. Versions v2.08 and
    v2.50 are provided, but you can easily add a new one under
    AvisynthSwitcher\versions\Avisynth 2.x.x.

-   Some other ways are described `here`_.


VirtualdubMod, WMP6.4, CCE and other programs crash every time on exit (when
previewing an avs file)?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
~~~~~~~~~~~~~~~~~~~~~~~~

This problem can be caused by certain plugins in your (autoloading) plugin
folder. The solution is to move the problematic plugins outside your plugin
folder and load them manually.


My computer seems to crash at random during a second pass in any encoder?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

AviSynth is highly optimized. As a consequence it is possible that your
computer seems to crash at random during a second pass. Try running the
`Prime95`_ stress test for an hour, to check if your system is stable. If
this test fails (or your computer locks up) make sure that your computer is
not overclocked and lower your bus speed of your processor in steps of (say)
five MHz till the crashes are gone.


Is there a command line utility for encoding to DivX/XviD using AviSynth?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

-   There is a command line utility called `AVS2AVI`_ (and AVS2AVI GUI)
    for encoding to DivX / XviD using AviSynth. [`discussion`_]
-   `xvid_encraw`_ for encoding to XviD in M4V. Use `mp4box`_ or `YAMB`_
    to mux it into MP4.


Does AviSynth have a GUI (graphical user interface)?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

AviSynth doesn't have a full fledged gui, but several tools are available:

-   `VirtualDubMod`_: The following AviSynth related utilities are
    present:

    -   'Open via AVISynth' command: This allows you to open any AviSynth
    compatible video file by automatically generating a suitable script by a
    selectable template.
    -   AVS Editor (Hotkey Ctrl+E): Just open your AVS and under tools
    select "script editor". Change something and press F5 to preview the
    video.

-   AvisynthEditor: This is an advanced AviSynth script editor featuring
    syntax highlighting, auto-complete code and per version plugin definition
    files. `Here is a screenshot`_. It can be found `here`_. Discussion can
    be found on `Doom9.org forum`_.
-   `AVSGenie`_: AVSGenie allows the user to select a filter from a drop
    down list or from a popup menu. An editable page of parameters will then
    be brought into view, with a guide to the filter and it's parameters. A
    video preview window opens, showing "source" and "target" views. The
    source window, in simple cases, shows output of the first line of the
    script, generally an opened video file. The target window shows the
    output of the whole script. In this way, effects of filters can easily be
    seen. The line which represents the source window can be changed.
    Discussion can be found `here`_.
-   `SwiftAVS (by Snollygoster)`_: Another nice gui, formerly known as
    AviSynthesizer. [`discussion`_]
-   `AvsP`_: It's a tabbed script editor for Avisynth. It has many
    features common to programming editors, such as syntax highlighting,
    autocompletion, call tips. It also has an integrated video preview, which
    when coupled with tabs for each script make video comparisons a snap.
    What really makes AvsP unique is the ability to create graphical sliders
    and other elements for any filter's arguments, essentially giving
    Avisynth a gui without losing any of its powerful features. Discussion
    can be found `here`_.

|` Main Page`_ | **General Info** | `Loading Clips`_ | `Loading Scripts`_ |
`Common Error Messages`_ | `Processing Different Content`_ | `Dealing with
YV12`_ | `Processing with Virtualdub Plugins`_ |

$Date: 2008/10/26 14:18:53 $

.. _What is AviSynth?: #What_is_AviSynth.3F
.. _Who is developing AviSynth?: #Who_is_developing_AviSynth.3F
.. _Where can I download the latest versions of AviSynth?:
    #Where_can_I_download_the_latest_versions_of_AviSynth.3F
.. _What are the main bugs in these versions?:
    #What_are_the_main_bugs_in_these_versions.3F
.. _Where can I find documentation about AviSynth?:
    #Where_can_I_find_documentation_about_AviSynth.3F
.. _How do I install/uninstall AviSynth?:
    #How_do_I_install/uninstall_AviSynth.3F
.. _What is the main difference between v1.0x, v2.0x, v2.5x, v2.6x and
    v3.x?: #What_is_the_main_difference_between_v1.0x,_v2.0x,_v2.5x,_v2.6x_an
    d_v3.x.3F
.. _How do I know which version number of AviSynth I have?:
    #How_do_I_know_which_version_number_of_AviSynth_I_have.3F
.. _How do I make an AVS-file?: #How_do_I_make_an_AVS-file.3F
.. _Where do I save my AVS-file?: #Where_do_I_save_my_AVS-file.3F
.. _Are plugins compiled for v2.5x/v2.6x compatible with v1.0x/v2.0x and
    vice versa?: #Are_plugins_compiled_for_v2.5x/v2.6x_compatible_with_v1.0x/
    v2.0x_and_vice_versa.3F
.. _How do I use a plugin compiled for v2.0x in v2.5x?:
    #How_do_I_use_a_plugin_compiled_for_v2.0x_in_v2.5x.3F
.. _How do I switch between different AviSynth versions without re-
    install?:
    #How_do_I_switch_between_different_AviSynth_versions_without_re-
    install.3F
.. _VirtualdubMod, WMP6.4, CCE and other programs crash every time on
    exit (when previewing an avs file)?: #VirtualdubMod.2C_WMP6.4.2C_CCE_and_
    other_programs_crash_every_time_on_exit_.28when_previewing_an_avs_file.29
    .3F
.. _My computer seems to crash at random during a second pass in any
    encoder?: #My_computer_seems_to_crash_at_random_during_a_second_pass_in_a
    ny_encoder.3F
.. _Is there a command line utility for encoding to DivX/XviD using
    AviSynth?: #Is_there_a_command_line_utility_for_encoding_to_DivX.2FXviD_u
    sing_AviSynth.3F
.. _Does AviSynth have a GUI (graphical user interface)?:
    #Does_AviSynth_have_a_GUI_.28graphical_user_interface.29.3F
.. _Lukes homepage: http://neuron2.net/LVG/avisynth.html
    (http://neuron2.net/LVG/avisynth.html)
.. _mirror of his homepage:
    http://neuron2.net/www.math.berkeley.edu/benrg/index.html
    (http://neuron2.net/www.math.berkeley.edu/benrg/index.html)
.. _others: http://sourceforge.net/project/memberlist.php?group_id=57023
.. _here: http://sourceforge.net/project/showfiles.php?group_id=57023
    (http://sourceforge.net/project/showfiles.php?group_id=57023)
.. _AviSynth project page:
    http://sourceforge.net/tracker/?atid=482673&group_id=57023
    (http://sourceforge.net/tracker/?atid=482673&group_id=57023)
.. _Changelist: changelist.htm (Changelist)
.. _Main Page: http://avisynth.org/mediawiki/Main_Page (Main Page)
.. _Internal filters: corefilters.htm (Internal filters)
.. _AviSynth v3: http://avisynth.org/mediawiki/AviSynth_v3 (AviSynth v3)
.. _this: #How_do_I_know_which_version_number_of_AviSynth_I_have.3F
    (title)
.. _here: #Does_AviSynth_have_a_GUI_.28graphical_user_interface.29.3F
    (title)
.. _here: #How_do_I_use_a_plugin_compiled_for_v2.0x_in_v2.5x.3F (title)
.. _warpsharp_2003_1103.cab: externalfilters/warpsharp.htm
.. _LoadOldPlugins: http://avisynth.org/mediawiki/LoadOldPlugins
    (LoadOldPlugins)
.. _here: http://www.lalternative.org (http://www.lalternative.org)
.. _here: http://forum.doom9.org/showthread.php?s=&threadid=45181
    (http://forum.doom9.org/showthread.php?s=&threadid=45181)
.. _Prime95: http://www.mersenne.org/freesoft.htm
    (http://www.mersenne.org/freesoft.htm)
.. _AVS2AVI: http://www.avs2avi.org/ (http://www.avs2avi.org/)
.. _discussion: http://forum.doom9.org/showthread.php?t=71493
    (http://forum.doom9.org/showthread.php?t=71493)
.. _xvid_encraw: http://forum.doom9.org/showthread.php?t=98469
    (http://forum.doom9.org/showthread.php?t=98469)
.. _mp4box: http://kurtnoise.free.fr/index.php?dir=mp4tools/
    (http://kurtnoise.free.fr/index.php?dir=mp4tools/)
.. _YAMB: http://forum.doom9.org/showthread.php?t=115459
    (http://forum.doom9.org/showthread.php?t=115459)
.. _VirtualDubMod: http://avisynth.org/mediawiki/VirtualDubMod
    (VirtualDubMod)
.. _Here     is a screenshot:
    http://www.lalternative.org/img/AvisynthEditor.gif
    (http://www.lalternative.org/img/AvisynthEditor.gif)
.. _Doom9.org     forum:
    http://forum.doom9.org/showthread.php?s=&threadid=49487
    (http://forum.doom9.org/showthread.php?s=&threadid=49487)
.. _AVSGenie: http://www.yeomanfamily.demon.co.uk/avsgenie/avsgenie.htm
    (http://www.yeomanfamily.demon.co.uk/avsgenie/avsgenie.htm)
.. _here: http://forum.doom9.org/showthread.php?s=&threadid=54090
    (http://forum.doom9.org/showthread.php?s=&threadid=54090)
.. _SwiftAVS     (by Snollygoster):
    http://sourceforge.net/project/showfiles.php?group_id=74272
    (http://www.swiftavs.net)
.. _discussion: http://forum.doom9.org/showthread.php?s=&threadid=48326
    (http://forum.doom9.org/showthread.php?s=&threadid=48326)
.. _AvsP: http://avisynth.org/qwerpoi/Download.html
.. _here: http://forum.doom9.org/showthread.php?t=129385
.. _ Main Page: faq_sections.htm (AviSynth FAQ)
.. _Loading Clips: faq_loading_clips.htm (FAQ loading clips)
.. _Loading Scripts: faq_frameserving.htm (FAQ frameserving)
.. _Common Error Messages: faq_common_errors.htm (FAQ common errors)
.. _Processing Different Content: faq_different_types_content.htm (FAQ
    different types content)
.. _Dealing with YV12: faq_yv12.htm (FAQ YV12)
.. _Processing with Virtualdub Plugins: faq_using_virtualdub_plugins.htm
    (FAQ using virtualdub plugins)
