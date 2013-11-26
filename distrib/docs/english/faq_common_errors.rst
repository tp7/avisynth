
AviSynth FAQ - Some common error messages
=========================================


Contents
--------

1.  ` I got the message "LoadPlugin: unable to load "xxx" is not an
    AviSynth 1.0/AviSynth 2.0 plugin"?`_
2.  ` When frameserving I got the following message: "Script error, there
    is no function named "xxx (some filter)"" ?`_
3.  ` I installed AviSynth and get the following error message: "Couldn't
    locate decompressor for format 'YV12' (unknown)."?`_
4.  ` When encoding I got the following error "ACM failed to suggest a
    compatible PCM format"?`_
5.  ` When encoding I got the following error: "framesize xxx not
    supported"?`_
6.  ` When frameserving I got the following message: "AVISource: couldn't
    locate a decompressor for fourcc (...)"?`_
7.  ` When frameserving I got the following message: "DirectShowSource:
    Could not open as video or audio
Video Returned: "DirectShowSource: the filter graph manager won't talk to
me""?`_
8.  ` I am trying to load a script that has a path name with a mix of
    japanese characters (someone's name) and Ascii test. I got an import
    error and the path that is displayed has some strange characters (not the
    japanese characters)?`_
9.  ` When frameserving I got the following message: " CAVIStreamSynth:
    System exception - Access Violation at 0x0, reading from 0x0"?`_
10. ` When frameserving I got a message similar to: "Avisynth open
    failure: Script error: Invalid arguments to function "xxx (some filter)"
    (I:\Video.avs, line 5)"`_


I got the message "LoadPlugin: unable to load "xxx (some plugin)" is not an
AviSynth 1.0/AviSynth 2.0 plugin"?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

You are using a plugin which is not compatiable with that version of
AviSynth. As explained `here`_, plugins compiled for AviSynth v2.5 are not
compatible with AviSynth v1.0x/v2.0x and vice versa.


When frameserving I got the following message: "Script error, there is no
function named "xxx (some filter)"" ?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

You probably installed/registered a version of AviSynth which doesn't contain
that specific filter. Make sure that there are no other versions floating
around on your hard disk (there's a possibility that a version will be
registered while it is not in your system directory). Make sure that the
latest stable version is registered, see also `here`_.


I installed AviSynth and got the following error message: "Couldn't locate
decompressor for format 'YV12' (unknown)."?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Install a codec which supports YV12. DivX5 or one of the recent `XviD builds
of Koepi`_ or `Helix YUV codec`_ or some other (ffvfw, ffdshow). If that
still doesn't work, modify your registry as explained in the next question.


When encoding I got the following error "ACM failed to suggest a compatible
PCM format"?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
~~~~~~~~~~~~~

This error means that you are using AviSource to open your AVI file, but you
don't have an ACM codec to decode the audio stream. The most common problem
is that your audio is an AC3 or a MP3 stream, but you don't have the
corresponding ACM codec installed. It can also happen that your audio is a
"crippled" (that is, with an incorrect header) MP3 `[1]`_ `[2]`_ `[3]`_.

There are several solutions for this problem:

-   Get the proper ACM codec. You can use `GSpot`_ to find out which
    audio stream you are dealing with. The needed ACM codecs can be found
    `here`_.
-   Demux your audio with an application like `AVI-Mux GUI`_ or
    `VirtualDub`_, and import your audio with a specific plugin. See also
    `here.`_
-   Use `DirectShowSource`_ to open the audio. Install `ffdshow`_ and
    enable the specific audio format in the "Audio Decoder Properties" tab.
    Create the following script:

::Vid = AviSource("Blah.avi", audio=false)
    Aud = DirectShowSource("Blah.avi", video=false)
    AudioDub(Vid, Aud)
When encoding I got the following error: "framesize xyz x 56 not supported"?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

This usually is an indicator of a script error, where the input is actually
the error message being displayed. Here, xyz is the length of the error
message text and 56 is the height (xyz will vary depending on the error
message whilst the height will always be 56 pixels). Your encoder is seeing
the error message as an RGB32 input source and hence the error. Opening the
script with WMP or VirtualDub should display the error message. Fix the error
in the script and retry to encode.


When frameserving I got the following message: "AVISource: couldn't locate a
decompressor for fourcc (...)"?
~~

Usually, this error message shows up if you don't have the right VfW codec
installed for decoding your video. Get `Gspot`_ to find out which codec you
need. Get, for example, `XviD`_ for your MPEG-4 ASP clips and `Cedocida
codec`_ for your DV clips. If you have problems finding the right one, ask
around on the video forums.

But it can also show up if you call `AviSource`_ too many times. The dll for
the decompression codec is loaded separately for every AviSource call.
Eventually an OS-imposed limit is reached, the codec can't be loaded and you
get that error message. More discussion can be found `here`_. A good solution
is to use a number of scripts (keeping each below the problematic limit of
avi calls) and encode them separately, and join them afterwards in some
application.


When frameserving I got the following message: "DirectShowSource: Could not
open as video or audio
Video Returned: "DirectShowSource: the filter graph manager won't talk to
me""?
~

This is a common error that occurs when DirectShow isn't able to deliver any
format that is readable to AviSynth. Try creating a filter graph manually.
See if you are able to construct a filter graph that delivers any output that
AviSynth can open. If not, you might need to download additional DirectShow
filters that can deliver correct material. If you can play the graph in
`GraphEdit`_, make sure to remove the video and audio renderers, before
saving the graph and opening it in AviSynth. Some examples can be found
`here`_.


I am trying to load a script that has a path name with a mix of japanese
characters (someone's name) and Ascii test. I got an import error and the
path that is displayed has some strange characters (not the japanese
characters)?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

AviSynth has problems with non-ANSI chars on filenames. It only supports `8
bit character ANSI text`_. Some discussion about this: `[4]`_ and `[5]`_.


When frameserving I got the following message: "CAVIStreamSynth: System
exception - Access Violation at 0x0, reading from 0x0"?
~~

Access Violation at 0x0, reading from 0x0 is usually caused by running out of
memory (memory leak ???). It can be caused by a plugin which is leaking
memory, but apparently it can also be caused by other things (codecs,
applications ???) [`1`_] [`2`_]. Add SetMemoryMax(...) at the beginning of
the script. If that doesn't help, report the issue in the doom9 forums, and
we will try to help finding the cause of it.


When frameserving I got a message similar to: "Avisynth open failure: Script
error: Invalid arguments to function "xxx (some filter)" (I:\Video.avs, line
5)"
~~~~~~~~~~~~~~~~~~~~~~~

It means you are passing incorrect arguments (that is of the correct type) to
your script, filter or plugin. For example:

::# passing a float (2.0), while `Loop`_ expects an int:
    Loop(clip, 2.0) ::# passing three clips to `Overlay`_ instead of two:
    AviSource("anime_raw.avi")
    karaoke = AviSource("karaoke.avi")
    Trim(0,999) + Trim(1000,1030).Overlay(last, karaoke,
    mask=sign.ShowAlpha()) + Trim(1031,0)
    # last should be omitted as argument to Overlay ::# implicit 'last'
    not defined
    v = AviSource("myvid.avi")
    Trim(100, 199)
    # need to use v.Trim(...) here

So make sure the passed arguments are of the correct type and read the
corresponding documentation if necessary.

|` Main Page`_ | `General Info`_ | `Loading Clips`_ | `Loading Scripts`_ |
**Common Error Messages** | `Processing Different Content`_ | `Dealing with
YV12`_ | `Processing with Virtualdub Plugins`_ |

$Date: 2010/11/28 18:47:26 $

.. _ I got the message "LoadPlugin: unable to load "xxx" is not an
    AviSynth 1.0/AviSynth 2.0 plugin"?: #unable_load_plugin
.. _ When frameserving I got the following message: "Script error, there
    is no function named "xxx (some filter)"" ?: #error_no_function
.. _ I installed AviSynth and get the following error message: "Couldn't
    locate decompressor for format 'YV12' (unknown)."?: #no_decoder
.. _ When encoding I got the following error "ACM failed to suggest a
    compatible PCM format"?: #no_acm_codec
.. _framesize xxx not supported"?: #error_framesize
.. _?: #no_decoder2
.. _?: #error_dss
.. _ I am trying to load a script that has a path name with a mix of
    japanese characters (someone's name) and Ascii test. I     got an import
    error and the path that is displayed has some strange characters (not the
    japanese characters)?: #error_ascii
.. _?: #CAVIStreamSynth
.. _ (I:\Video.avs, line 5): #InvalidArguments
.. _here:
    faq_general_info.htm#How_do_I_use_a_plugin_compiled_for_v2.0x_in_v2.5x.3F
.. _here: faq_general_info.htm#How_do_I_know_which_version_number_of_AviS
    ynth_I_have.3F
.. _XviD builds of Koepi: http://www.xvid.org/
.. _Helix YUV codec:
    http://forum.doom9.org/showthread.php?s=&threadid=56972
.. _[1]: http://forums.virtualdub.org/index.php?act=ST&f=4&t=802&hl=0055
.. _[2]: http://forums.virtualdub.org/index.php?act=ST&f=3&t=10931&hl=unk
    nown%20tag%200055&st=15
.. _[3]: http://forum.doom9.org/showthread.php?t=94760
.. _GSpot: http://www.headbands.com/gspot/
.. _here: advancedtopics/importing_media.htm
.. _AVI-Mux     GUI: http://www.alexander-noe.com/video/amg/
.. _VirtualDub: http://www.virtualdub.org
.. _here.: faq_loading_clips.htm
.. _DirectShowSource: corefilters/directshowsource.htm (DirectShowSource)
.. _ffdshow: http://ffdshow-tryout.sourceforge.net/
.. _Cedocida codec: http://forum.doom9.org/showthread.php?t=94458
.. _AviSource: corefilters/avisource.htm (AviSource)
.. _here: http://forum.doom9.org/showthread.php?t=131687
.. _GraphEdit: http://avisynth.org/mediawiki/GraphEdit (GraphEdit)
.. _here: advancedtopics/importing_media.htm#graphs (Importing media)
.. _8 bit character ANSI text: http://en.wikipedia.org/wiki/ASCII
.. _[4]: http://forum.doom9.org/showthread.php?t=110467
.. _[5]: http://forum.doom9.org/showthread.php?t=131419
.. _1: http://forum.doom9.org/showthread.php?t=123195
.. _2: http://forum.doom9.org/showthread.php?t=128403
.. _Loop: corefilters/loop.htm
.. _Overlay: corefilters/overlay.htm
.. _ Main Page: faq_sections.htm (AviSynth FAQ)
.. _General Info: faq_general_info.htm
.. _Loading Clips: faq_loading_clips.htm (FAQ loading clips)
.. _Loading Scripts: faq_frameserving.htm (FAQ frameserving)
.. _Processing Different Content: faq_different_types_content.htm (FAQ
    different types content)
.. _Dealing with YV12: faq_yv12.htm (FAQ YV12)
.. _Processing with Virtualdub Plugins: faq_using_virtualdub_plugins.htm
    (FAQ using virtualdub plugins)
