
Avisynth Frequently Asked Questions
------------------------------------

**Remark**: a more recent version can be found `here`_ and at
`http://www.avisynth.org`_

The faq is divided into four sections: a general section, one related to
frameserving, one related to filters and plugins, and one related to
importing VirtualDub filters. Recently, the old stuff "related to AviSynth
v2.06 and older versions" is removed. Thus, if you have problems, make sure
that you install a more recent version of AviSynth.

**`S1: About AviSynth`_**

**`S2: AviSynth and frameserving`_**

**`S3: Filters, plugins and colorspaces`_**

**`S4: Importing filters from VirtualDub`_**




**`S1: About AviSynth:`_**

**`Q1.1: What is AviSynth ?`_**
**`Q1.2: Who is developing AviSynth ?`_**
**`Q1.3: Where can I download the latest versions of AviSynth ?`_**
**`Q1.4: What are the main bugs in these versions ?`_**
**`Q1.5: Where can I find documentation about AviSynth ?`_**
**`Q1.6: How do I install/uninstall AviSynth ?`_**
**`Q1.7: Is there any difference between v1.0x, v2.0x or v2.5x ?`_**
**`Q1.8: Are plugins compiled for v2.5x compatible with v1.0x/v2.0x and vice
versa ?`_**
**`Q1.9: Which encoding programs support YV12 ?`_**
**`Q1.10: How do I use v2.5x if the encoding programs can't handle YV12 (like
Virtualdub, TMPGEnc or CCE SP) ?`_**
**`Q1.11: How do I use with AviSynth v2.5 with Gordian Knot?`_**
**`Q1.12: What are the main advantages of processing/encoding in YV12 ?`_**
**`Q1.13: Is there a command line utility for encoding to DivX/XviD using
AviSynth ?`_**
**`Q1.14: Where can I find VCF2AVS ?`_**
**`Q1.15: How do I use a plugin compiled for v2.0x in v2.5x ?`_**
**`Q1.16: How do I switch between differents Avisynth versions without re-
install ?`_**
**`Q1.17: How do I make an AVS-file ?`_**
**`Q1.18: Where do I save my AVS-file ?`_**
**`Q1.19: How do I know which version number of AviSynth I have ?`_**
**`Q1.20: Does AviSynth have a GUI (graphical user interface) ?`_**
**`Q1.21: I got the message "LoadPlugin: unable to load "xxx" is not an
AviSynth 1.0/AviSynth 2.5 plugin ?`_**
**`Q1.22: How do I know which colorspace I'm using at a given place in my
script ?`_**
**`Q1.23: I installed AviSynth v2.5 and DivX5 (or one of the latest Xvid
builds of Koepi), all I got is a black screen when opening my avs in
Virtualdub/VirtualdubMod/CCE/TMPGEnc ?`_**
**`Q1.24: My computer seems to crash at random during a second pass in any
encoder ?`_**
**`Q1.25: VirtualdubMod, WMP6.4, CCE and other programs crash every time on
exit (when previewing an avs file) ?`_**
**`Q1.26: Are there any lossless YV12 codecs, which I can use for capturing
for example?`_**

**`S2: AviSynth and frameserving:`_**

**`Q2.1: What is frameserving and what is it good for ?`_**
**`Q2.2: How do I use AviSynth as a frameserver ?`_**
**`Q2.3: How do I frameserve my AVS-file to encoder/application X ?`_**
**`Q2.4: Problems when Encoder X reads AVS-files ?`_**
**`Q2.5: How do I frameserve from Premiere/Ulead/Vegas to AviSynth ?`_**
**`Q2.6: When frameserving I got the following message: "Script error, there
is no function named "xxx (the name of some filter)"" ?`_**
**`Q2.7: I get an unrecognized exception error trying to load an avs file
with VirtualDub, using dvd2avi v1.77.3 ?`_**
**`Q2.8: How do I load my clip into AviSynth (video) ?`_**
**`Q2.9: How do I load my clip into AviSynth (audio) ?`_**
**`Q2.10: Can I import an audio file other than a WAV-file?`_**
**`Q2.11: How do I join video and audio ?`_**
**`Q2.12:  I get an unrecognized exception in the line where I use
DirectShowSource?`_**

**`S3: Filters, plugins and colorspaces:`_**

**`Q3.1: What is RGB/YUV-colorspace ?`_**
**`Q3.2: In which colorspaces do AviSynth and the internal filters work ?`_**
**`Q3.3: How do I load a plugin in to AviSynth ?`_**
**`Q3.4: Where can I download external filters for AviSynth v1.0x/v2.0x ?`_**
**`Q3.5: Where can I download external filters for AviSynth v2.5x ?`_**
**`Q3.6: Where can I download utilities for AviSynth ?`_**
**`Q3.7: How do I convert between the colorspaces ?`_**
**`Q3.8: What/when do I care when filter X works in RGB- or YUV-space ?`_**
**`Q3.9: How do I use and where can I get the "Subtitler" and "BMP Loader"
plugins ?`_**

**`S4: Importing filters from VirtualDub:`_**

**`Q4.1: Where can I download the latest version of scripts which import
filters from VirtualDub ?`_**
**`Q4.2: Which filters are imported ?`_**
**`Q4.3: Do these scripts work in RGB-space or in YUV-space ?`_**
**`Q4.4: How do I make such a script ?`_**


**S1: About Avisynth:**


**Q1.1: What is AviSynth ?**

A: AviSynth (AVI SYNTHesizer) is a frameserver. An excellent discription is
given on ` Lukes homepage`_:

"AviSynth is a very useful utility created by Ben Rudiak-Gould. It provides
many options for joining and filtering videos. What makes AviSynth unique is
the fact that it is not a stand-alone program that produces output files.
Instead, AviSynth acts as the "middle man" between your videos and video
applications.

Basically, AviSynth works like this: First, you create a simple text document
with special commands, called a script. These commands make references to one
or more videos and the filters you wish to run on them. Then, you run a video
application, such as VirtualDub, and open the script file. This is when
AviSynth takes action.  It opens the videos you referenced in the script,
runs the specified filters, and feeds the output to video application. The
application, however, is not aware that AviSynth is working in the
background.  Instead, the application thinks that it is directly opening a
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




**Q1.2: Who is developing AviSynth ?**

A: AviSynth (up to v1.0b) is developed by Ben Rudiak-Gould, see
`http://math.berkeley.edu/~benrg/avisynth.html`_.  Ben stopped developing and
Edwin van Eggelen continued, see
`http://www.videotools.net/uk/download.php`_. His latest release is version
v1.0b6 which can be found on Edwins homepage given above.

Some versions appeared on the AviSynth forum, for example `v1.0b7a by
Divine`_ and `v1.0b7d by Dividee`_.

In the beginning of July 2002 there was a `second revision (v2.0x)`_ of the
sourceforge project.  (In the `first sourceforge project`_ didn't happen
much.)

The most recent version is v2.5x series, weekly builds v2.5.0-2.5.5 by
leading developer Klaus Post were `here`_. The main developer of AviSynth
v2.5.6-2.5.7 is Ian Brabham (IanB). Many other people contributed to
AviSynth. For partial list see (play) `Authors.avs`_ file. Official
`memberlist`_ at sourceforge project:
Alex_e_Basta aka alex_e_basta (doc writer), David Pierre aka bidoche
(developer), Frank Skare aka dolemite1 (developer), Vincent TORRI aka doursse
(developer), Alexander Balakhnin aka fizick (doc writer), Ian Brabham aka
ianb1957 (developer, admin), Jonathan Ernst aka jernst (doc writer), kostarum
(translator), Cedric PAILLOT aka macpaille (doc writer), Donald Graft aka
neuron2 (project manager), Richard Berg aka richardberg (project manager),
Klaus Post aka sh0dan (developer, admin), Andrew Dunstan aka squid_80
(developer), Tonny S Petersen aka tsp42 (developer), Ernst Peche aka
warpenterprises (doc writer), Wilbert Dijkhof aka wilbertd (project manager,
doc writer).
AviSynth is free open source program distributed under GNU General Public
License as published by the Free Software Foundation.

**Q1.3: Where can I download the latest versions of AviSynth ?**

A: See `Q1.2`_. It is also contained in the DVD2SVCD package and on the
download page of Doom (these might be not be the newest versions of
AviSynth).
Latest versions of AviSynth can now be downloaded at `sourceforge page.`_

**Q1.4: What are the main bugs in these versions ?**

A: The latest versions:

v1.0b5: `Dissolve`_ doesn't work, BicubicResize doesn't work properly.
v1.0b6: ?
v1.0b7a/v1.0b7d: `Dissolve`_ doesn't work.
v2.01: ?
v2.02: `Layer`_ and `MergeChroma`_ don't work.
v2.05: `Loop`_ doesn't work when loading a clip without sound.
v2.07/v2.50: `SegmentedAviSource`_ doesn't load the avi's if the last empty
segment isn't deleted.

v2.50 beta; `AviSynthTwoFiveZeroBugs`_.
v2.51 beta; `AviSynthTwoFiveOneBugs`_.
v2.52; `AviSynthTwoFiveTwoBugs`_.

other bugs can be found in the documentation on the project page, see
`Q1.5`_.


**Q1.5: Where can I find documentation about AviSynth ?**

A: Documentation about the filters of AviSynth can be found on this site
`http://www.avisynth.org/`_, and also on the `filters`_ page. For a tutorial
on avisynth scripting, have a look at `this page`_. **You should read these
documents before posting to the forum** (but it's OK to post if you have
trouble understanding them).


**Q1.6: How do I install/uninstall AviSynth ?**

A: In v2.05 or older versions: move avisynth.dll to your system/system32
directory and run install.reg. Starting from v2.06 AviSynth comes with an
auto installer. **Also make sure you have no other versions of AviSynth
floating around on your harddisc, because there is a change that one of those
versions will be registered. Remove them if necessary.** For uninstalling
AviSynth go to "program", "AviSynth 2" and select "Uninstall AviSynth".


**Q1.7: Is there any difference between v1.0x, v2.0x or v2.5x ?**

A: The versions v1.0x and v2.0x are compatible (the main difference is that
v2.0x doesn't contain IPCSource, while it contains other filters which are
not present in v1.0x).  The main difference with v2.5x is that the internal
structure of AviSynth has changed (YV12 and multichannel support) with the
consequence that **external plugins compiled for v1.0x or v2.0x will not work
for v2.5x and vice versa**.


**Q1.8: Are plugins compiled for v2.5x compatible with v1.0x/v2.0x and vice
versa ?**

A: As explained in `Q1.7`_ that is not the case.  However it is possible to
use a v1.0x/v2.0x plugin in v2.5x, see `Q1.15`_.


**Q1.9: Which encoding programs support YV12 ?**

A: There are several options for encoding to DivX/XviD:

1.  There is a modified version (called VirtualdubMod) which has YV12
    support:  This modification (by pulco-citron, Suiryc and Belgador) has
    OGM and AVS-preview support.  It can be downloaded from `here`_.  In
    order to use the YV12 support (without doing any color conversions) you
    have to load your AVI in VirtualdubMod and select "**fast recompress**".
2.  VirtualDub support YV12 starting from v1.5.6.  In order to use the
    YV12 support (without doing any color conversions) you have to load your
    AVI in VirtualDub and select "**fast recompress**".
3.  For easy (and fast) YV12 support, you can also try out the new
    commandline compressor: AVS2AVI, see also `Q1.21`_.


**Q1.10: How do I use v2.5x if the encoding programs can't handle YV12 (like
Virtualdub, TMPGEnc or CCE SP) ?**

A: Using Virtualdub you have to add "`ConvertToYUY2`_" to your script or you
have to install a YV12 decompressor like DivX5 or one of the recent XviD
builds of Koepi (`XviD-04112002-1 or newer`_).  Enabling "fast recompress"
implies that there will be a YV12 --> YUY2 --> YV12 conversion.  (DivX3/4
also supports YV12, except that PIV users could experience `crashes`_ when
encoding to DivX4 in YV12.)

Using TMPGEnc you have to add the line `ConvertToRGB24`_ to your script, and
for CCE SP you need to add the line `ConvertToYUY2`_ to your script, since
Windows has no internal YV12 compressor.  You can also install DivX5 one of
the recent XviD builds of Koepi (`XviD-04112002-1 or newer`_) which will
decompress the YV12-AVI for you when loading the avi in TMPGEnc or CCE SP.


**Q1.11: How do I use with AviSynth v2.5 with Gordian Knot?**

- If you are using GKnot 0.26 you have to rename mpeg2dec3.dll (the one for
AviSynth v2.5) to mpeg2dec.dll, and virtualdubmod.exe to virtualdub.exe
(keeping copies of the original exe and dll somewhere).

- If you are using GKnot 0.27 you can follow the same procedure as above, or
you can enter mpeg2dec3.dll as an alternative mpeg2dec.dll in the options
menu and rename virtualdubmod.exe to virtualdub.exe.

- But you can also try the new GKnot 0.28.

If you are using VirtualdubMod 1.4.13.1 older and experience problems,
download the latest `prerelease`_.


**Q1.12: What are the main advantages and processing/encoding in YV12?**

A: There are two advantages:

-   *speed increase:*

It depends entirely on the external plugins whether they will have YV12
support or not.  If they have then speed increases like 25-35 percent are
expected.  Of course there will only be a large speed increase if both your
source and target are in YV12, for example in DVD to DivX/Xvid conversions.
-   *no color conversions:*

The color information doesn't get interpolated (so often) and thus stays more
realistic.  Even if you have to do color conversions (because your are
encoding with CCE SP or TMPGEnc) you have the advantage that putting off the
YV12->YUY2 (or RGB24 for TMPGEnc) conversion until the end of the script
allows you to first IVTC or Deinterlace to create progressive frames.  But
the YV12 to YUY2 conversion for progressive frames maintains more chroma
detail than it does for interlaced or field based frames.


**Q1.13: Is there a command line utility for encoding to DivX/XviD using
AviSynth ?**

A: As explained in `Q1.9`_ there is a command line utility called `AVS2AVI`_
(and AVS2AVI GUI) for encoding to DivX/XviD using AviSynth.


**Q1.14: Where can I find VCF2AVS ?**

A: VCF2AVS is a nice litte tool to convert vcf to avs files. You can edit
your captures in vdub (basically cutting, cropping and resizing), then edit
the resulting avs. Be carefull since there are two versions floating around:

-   VCF2AVS by Darksoul71 which can be found `here`_.

-   VCF2AVS by BB (more basic) which can be found `here`_.

Try them both and look which one fullfills your needs :)


**Q1.15: How do I use a plugin compiled for v2.0x in v2.5x ?**

A: In `WarpSharp-package for AviSynth v2.5x`_ you will find a plugin called
"LoadPluginEx.dll". **When using an older version of LoadPluginEx.dll, don't
move this plugin to your plugin dir.  But move it to a separate dir,
otherwise VirtualdubMod and WMP6.4 will crash on exist.**  This will enable
you using v2.0x plugins in v2.5x.  An example script (using the v2.0x plugin
Dust by Steady):

*LoadPlugin("C:\Program Files\avisynth2_temp\plugins\LoadPluginEx.dll")*
*LoadPlugin("C:\Program Files\avisynth2_temp\plugins\dustv5.dll")*

*AviSource("D:\clip.avi").ConvertToYUY2*
*PixieDust(5)*


**Q1.16: How do I switch between differents AviSynth versions without re-
install ?**

A:

-   You can use AvisynthSwitcher available `here`_.  Versions 2.08 and
    2.50 are provided, but you can easily add a new one under
    AvisynthSwitcher\versions\Avisynth 2.x.x.
-   Some other ways are described `here`_.


**Q1.17: How do I make an AVS-file ?**

A: See `Q1.19`_ (using the text editor you prefer).


**Q1.18: Where do I save my AVS-file ?**

A: Anywhere on your harddrive.


**Q1.19: How do I know which version number of AviSynth I have ?**

A: Open a text-editor, for example notepad. At the following line

`Version`_

and save the file with the extension "avs".  Save for example as version.avs
(make sure that the extension is "avs" and not "txt").  Open the file in an
application which can read AVI-files, for example WMP 6.4. The version number
will be displayed.


**Q1.20: Does AviSynth have a GUI (graphical user interface) ?**

A: Several nice tools are available:

-   VirtualdubMod, see also `Q1.9`_.  Regarding to AviSynth the following
    utilities are added:

-   'Open via AVISynth' command. This allows you to open any AviSynth
    compatible video file by automatically generating a suitable script by a
    selectable template.

-   AVS Editor (Hotkey Ctrl+E): Just open your AVS and under tools select
    "script editor". Change something and press F5 to preview the video.



-   `AvisynthEditor`_, an advanced AviSynth script editor featuring
    syntax highlighting, auto-complete code and per versions plugin
    definitions files. Here is a `screenshot`_.  It can be found `here`_.
    Discussion can be found on `Doom9.org forum`_.


-   `AVSGenie`_: AVSGenie allows the user to select a filter from a drop
    down list or from a popup menu. An editable page of parameters will then
    be brought into view, with a guide to the filter and it's parameters. A
    video preview window opens, showing "source" and "target" views.  The
    source window, in simple cases, shows output of the first line of the
    script, generally an opened video file. The target window shows the
    output of the whole script. In this way, effects of filters can easily be
    seen. The line which represents the source window can be changed.
    Discussion can be found `here`_.


-   `SwiftAVS (by Snollygoster)`_: Another nice gui, formerly known as
    AviSynthesizer. [`discussion`_]


**Q1.21: I got the message "LoadPlugin: unable to load "xxx" is not an
AviSynth 1.0/AviSynth 2.5 plugin" ?**

A: You are using a plugin which is not compatiable with that version of
AviSynth.  Have a look at `Q1.8`_.


**Q1.22: How do I know which colorspace I'm using at a given place in my
script ?**

A: To see which colorspace you are using at a given place in your script,
add:

`Info`_

... and AviSynth will give you much information about colorspace amongst
other things!


**Q1.23: I installed AviSynth v2.5 and DivX5 (or one of the latest Xvid
builds of Koepi), all I got is a black screen when opening my avs in
Virtualdub/!VirtualdubMod/CCE/TMPGEnc ?**

A: Ok, apperently your video is not decompressed by DivX5 (or XviD).  Go to
your windows-dir and rename a file called MSYUV.DLL, or add the following to
your registry file:

*REGEDIT4*

*[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Drivers32]*
*"VIDC.YV12"="divx.dll"*

Replace "divx.dll" by "xvid.dll" for XviD.


**Q1.24: My computer seems to crash at random during a second pass in any
encoder ?**

A : AviSynth (especially v2.5x) is highly optimized. As a consequence it is
possible that your computer seems to crash at random during a second pass.
Try running the [`Prime95`_] stress test for an hour, to check if your system
is stable. If this test fails (or your computer locks up) make sure that your
computer is not overclocked and lower your bus speed of your processor in
steps of (say) five MHz till the crashes are gone.


**Q1.25:VirtualdubMod, WMP6.4, CCE and other programs crash every time on
exit (when previewing an avs file) ?**

A: This problem arises if you got an older version of LoadPluginEx.dll (or
WarpSharp.dll) of the WarpSharp package in your plugin dir. The solution is
to move it outside the plugin directory and load it manually. I hope that the
maker of this plugin also noticed this ...

**Q1.26: Are there any lossless YV12 codecs, which I can use for capturing
for example?**

A: There are several of them:

1.  `VBLE codec (by MarcFD)`_: an huffyuv based encoder
2.  `LocoCodec (by TheRealMoh)`_:
3.  `MJPEG codec`_: Leaves a small logo in the right upper side of the
    clip.


**S2: AviSynth and frameserving:**


**Q2.1: What is frameserving and what is it good for ?**

A: An excellent discription is found on ` Lukes homepage`_:

"Frameserving is a process by which you directly transfer video data from one
program on your computer to another. No intermediate or temporary files are
created. The program that opens the source file(s) and outputs the video data
is called the frameserver. The program that receives the data could be any
type of video application.

There are two main reasons that you would want to frameserve a video:


1.  Save Disk Space:

Depending the on the frameserving application, you can usually edit/process
your video as it is being frameserved. Because frameserving produces no
intermediate files, you can use a frameserver to alter your videos without
requiring any additional disk space. For example, if you wanted to join two
video files, resize them, and feed them to another video application,
frameserving would allow you to do this without creating a large intermediate
file.

2.  Increased Compatibility:

To the video application that's receiving the frameserved video, the input
looks like a relatively small, uncompressed video file. However, the source
file that the frameserver is transferring could actually be, for example, a
highly compressed MPEG-1 video. If your video application doesn't support
MPEG-1 files, it's not a problem because the application is just receiving
standard uncompressed video from the frameserver. This feature of
frameserving enables you to open certain types of files in an application
that wouldn't normally support them.


Furthermore, because the video application is being fed the source video one
frame at a time, it doesn't know anything about the file size of the source
video. Therefore, if your application has 2 GB or 4 GB limit on input file
size, it won't have any effect on your frameserved video. You could feed 100
GB of video via a frameserver to an application limited to 2 GB and it
wouldn't cause a problem."


**Q2.2: How do I use AviSynth as a frameserver ?**

A: Write a script using a text editor. Load your clip (see `Q2.8`_) in
AviSynth, do the necessary filtering and load the AVS-file in
encoder/application X (must be an encoder or application which can read AVI-
files, see `Q2.3`_ and `Q2.4`_).


**Q2.3: How do I frameserve my AVS-file to encoder/application X ?**

A:

-   Frameserving to TMPGEnc, CCE SP, VirtualDub or WMP6.4:

Just open your AVS-file in TMPGEnc, CCE SP, VirtualDub or WMP6.4 (or whatever
encoder/application you use) and have a look at `Q2.4`_.

-   Frameserving to VFAPI:

For VFAPI you need to install the `ReadAVS`_ plugin. Just copy ReadAVS.dll to
the VFAPI reader directory and open the reg-file ReadAVS.reg in notepad and
change the corresponding path. Save it, and doubleclick on it to merge it
with your registry-file.

-   Frameserving to Premiere or Ulead:

-   For frameserving to Premiere there exists an import plugin "IM-
    Avisynth.prm". The original version can be downloaded from `Bens site`_.
    A much improved version can be downloaded from the [`Video Editors Kit
    sourceforge page`_]. This works for Premiere 5.x,6.x and Pro at present.
    To install the import plugin move the IM-Avisynth.prm file into your
    Premiere "Plug-ins" directory.
-   You can also download a program called [`makeAVIS (included in the
    ffvfw codec package`_] (this is an AVI Wrapper), [`discussion`_]. Note
    that this program is included in the installation of AviSynth v2.52. For
    Ulead you must use this program.



-   Frameserving to Windows Media 9 Encoder:

Download Nic's Windows Media 9 Encoder and make sure you also installed the
Windows Media 9 codec. Both can be found `here`_.

**Q2.4: Problems when Encoder X reads AVS-files ?**

A:

1.  *Why can't I open my AVS-file in TMPGEnc (this happens in old
    versions of TMPGEnc) ?*

-   Install VFAPI plugin for TMPGEnc
-   Disable the direct show filters within TMPGEnc and turn off the
    VirtualDub proxy before frameserving.

-   Add "`ConvertToRGB24`_()" at the end of your AVS-file
-   Install `Huffyuv`_/`DivX5`_ codec so that it can do the decompression
    for you when loading an AVI in TMPGEnc.
-   Install the `ReadAVS`_ plugin for TMPGEnc



2.  *CCE SP crashes when reading an AVS-file, what to do ?*

-   If you're using Win2k then run CCE in WinNT4-SP5 compatibility mode.
-   If you're frameserving with AviSynth v1.0x/v2.0x put
    "`ResampleAudio`_(44100)" in your script, even if you don't have any
    audio in your AVS-file.
-   If you're frameserving with AviSynth v2.5x the ResampleAudio trick
    doesn't work anymore because it doesn't add a silent audio stream to your
    video clip.  Instead make a script (called "addaudio.avsi") as described
    `here`_, and put it in your plugin dir.



3.  *Encoders/players (like CCE SP v2.62/v2.64) will not read AVS-files
    ?*

Many "new" programs do NOT use the Windows functions to read the AVI-files.
If they do NOT use those standard Windows functions the AviSynth-script files
will not work. Known programs that do NOT use those routines are CCE SP
v2.62, Windows Media Encoder vx.x. Furthermore people report problems with
Windows Media Player 7.


-   Use CCE SP v2.50 and WMP6.4 (under "Program Files" and "Windows Media
    Player" you will find a file called "mplayer2.exe", this is WMP6.4). In
    case that you want to use Windows Media Encoder you can use the AVI
    Wrapper "makeAVIS" instead, see` Q2.3`_. For Windows Media Encoder 9 have
    a look at `Q2.3`_.
-   If you still want to use CCE SP v2.62 you can try the following:
    Frameserve to CCE SP v2.62 with VFAPI. Create an AVS script and then make
    a fake AVI with VFAPI (VFAPI accepts AVS-files, see `Q2.3`_, and can be
    downloaded from Dooms site).
-   Cinemacraft says that their CCE SP v2.66 can accept AviSynth scripts.
    So if you have this version you sould be safe.



4.  *Wrong YUY2 Codec causes colorspace errors on AviSynth scripts
    feeding TMPGEnc?*

Some time ago I suddenly found that feeding TMPGEnc with an AviSynth script
resulted in what looked like a colorspace conversion error; as if the video
had been badly dithered down from 24 bit to 8 bit! (..)

If you have such problems add "`ConvertToRGB24`_" as the last line of your
script or have a look at the thread (and the suggested solutions) `colorspace
conversion errors`_.


**Q2.5: How do I frameserve from Premiere/Ulead/Vegas to AviSynth ?**

A: You can try the AviSynth compatible frameserver (import) for [`PluginPace
frameserver (by Satish Kumar)`_]: For frameserving from SonicFoundry Vegas
(and earlier Vegas Video/VideoFactory? versions), Adobe Premiere or Ulead
MediaStudio Pro to AviSynth. [`discussion`_].


**Q2.6: When frameserving I got the following message: "Script error, there
is no function named "xxx (the name of some filter)"" ?**

A: You probably installed/registered a version of AviSynth which doesn't
contain the filter.  Make sure that there are no other versions floating
around on your hard disc (there's a possibility that a version will be
registered while it is not in your system directory).  Check whether the
correct version is registered, see also `Q1.19`_.


**Q2.7: I get an unrecognized exception error trying to load an avs file with
VirtualDub, using dvd2avi v1.77.3 ?**

A: .d2v created with dvd2avi v1.77.3 is NOT compatible with mpeg2dec.dll! Use
v1.76 instead. If you still want to use v1.77.3, make sure that you have
AviSynth v2.5 installed and mpeg2dec3.dll v1.07 (or a more recent version).


**Q2.8: How do I load my clip into AviSynth (video) ?**

A: Make a script containing the lines (replace the filename and the path of
the filename):


1.  AVI-files (with uncompressed WAV, or CBR/VBR MP3-audio (starting from
    v2.04)):

*AviSource("d:\filename.avi")*
or disabling the audio:
*AviSource("d:\filename.avi", false)*

2.  AVI-files that AVISource doesn't support (for example "DV type I AVI-
    files"):

*DirectShowSource("d:\filename.avi")*
*DirectShowSource("d:\filename.mpg")*

3.  Have a look at the `Mpeg decoder plugins for AviSynth v1.0x/v2.0x`_
    and the `Mpeg decoder plugins for AviSynth v2.5x`_:

Using AviSynth v2.0x/AviSynth v2.5x and MPEGdecoder.dll:
*LoadPlugin("d:\MPEGdecoder.dll")*
*mpegsource("d:\filename.mpg")*

4.  MPEG2-files (extension m2p or m2v):

Have a look at the `Mpeg decoder plugins for AviSynth v1.0x/v2.0x`_ and the
`Mpeg decoder plugins for AviSynth v2.5x`_. Some examples:


-   Using AviSynth v2.0x and mpeg2dec.dll:

Make a DVD2AVI project file and save it (filename.d2v) and load this clip
into AviSynth:
*LoadPlugin("d:\mpeg2dec.dll")*
*mpeg2source("d:\filename.d2v")*

-   Using AviSynth v2.5x and MPEGdecoder.dll:

*LoadPlugin("d:\MPEGdecoder.dll")*
*mpegsource("d:\filename.m2p")*
or (only the video stream)
*LoadPlugin("d:\MPEGdecoder.dll")*
*mpegsource("d:\filename.m2v", -2, "raw")*

5.  VOB-files:

Have a look at the `Mpeg decoder plugins for AviSynth v1.0x/v2.0x`_ and the
`Mpeg decoder plugins for AviSynth v2.5x`_. Some examples:


-   Using AviSynth v2.0x and mpeg2dec.dll:

Make a DVD2AVI project file and save it (filename.d2v) and load this clip
into AviSynth:
*LoadPlugin("d:\mpeg2dec.dll")*
*mpeg2source("d:\filename.d2v")*

-   Using AviSynth v2.5x and MPEGdecoder.dll:

*LoadPlugin("d:\MPEGdecoder.dll")*
*mpegsource("d:\filename1.vob+d:\filename2.vob")*

6.  ATSC transport streams (extension *.trp or *.ts):



-   Using AviSynth v2.0x:

Download mpeg2dec2 and a special version of `dvd2avi`_.  Don't forget to
specify the video and audio pid's in the DVD2AVI.ini file:
*LoadPlugin("d:\mpeg2dec2.dll")*
*mpeg2source("d:\filename.d2v")*

-   Using AviSynth v2.0x/v2.5x:

Download mpeg2dec3 or mpegdecoder and a special version of `dvd2avi`_:
*LoadPlugin("d:\mpeg2dec3.dll")*
*mpeg2source("d:\filename.d2v")*
or if you want to used mpegdecoder:
*LoadPlugin("d:\mpegdecoder.dll")*
*mpegsource("d:\filename.d2v")*

If both methods fail you can try `HDTV2MPEG2`_ (produces non dvd compliant
mpeg2 files) to create a temporary mpeg2 file and import that in AviSynth
with dvd2avi. For demuxing AAC audio: use [`TSDemux`_]. The Moonlight
`Xmuxer`_ package has also a bunch of DirectShow filters that deal with
muxing and demuxing MPEG-1/2 TS and PVA files.



7.  PVA transport streams:

You are out of luck here.  AFAIK the only options are PVAStrumento and
`Xmuxer`_.

8.  d2v-files (DVD2AVI frameserver files):

*LoadPlugin("d:\mpeg2dec.dll")*
*mpeg2source("d:\filename.d2v")*

9.  vdr-files (VirtualDubs frameserver files):

*AVISource("d:\filename.vdr")*

10. ASF-files (the framerate has to be specified, right click on the file
    in windows explorer):

*DirectShowSource("d:\filename.asf", fps=15)*

11. tpr-files (TMPGEnc project files)

First note that the plugin GreedyHMA is proving to be a better IVTC solution
(not to mention *MUCH* easier) than TMPGEnc. So if you want to use TMPGEnc
for this get the GreedyHMA plugin (this plugin works in YUV-space).

If you still want to import a tpr-file into an AVS-file, there are two
possibilities:


-   The TMPGEnc plugin is contained in the VFAPI Plugin zip file (ends
    with -vfp.zip) which can be download from Dooms site. (This method
    doesn't always work, some encoders like CCE SP can't read them.)

*LoadVFAPIplugin("d:\TMPGenc.vfp","TMPGsource")*
*TMPGsource("d:\filename.tpr")*
*FlipVertical*
-   Import the tpr-file in VFAPI, create a fake avi and then load it into
    AviSynth (note that VFAPI works in RGB-space). See also
    `http://forum.doom9.org/showthread.php?s=&threadid=10007`_.



12. aup-files (AviUtl projects)

I don't know if it is possible to load it directly into AviSynth. Import the
aup-file in VFAPI, create a fake avi and then load it into AviSynth (note
that VFAPI works in RGB). See also
`http://forum.doom9.org/showthread.php?s=&threadid=10007`_.

13. QuickTime-files (see
    `http://forum.doom9.org/showthread.php?s=&threadid=23139`_):

Use DirectShowSource:
*DirectShowSource("d:\filename.mov")*
or if that doesn't work download a plugin (can be found in Dooms download
section):
*LoadVFAPIPlugin("C:\QTReader\QTReader.vfp", "QTReader")*
*QTReader("C:\quicktime.mov")*

14. AVS-files:

Just import it at the beginning of your script:
*Import("d:\filename.avs")*
In v2.05 or more recent version you can use the autoplugin loading.  Just
move your AVS-file in the plugindir containing the other (external) plugins,
and rename (since v.2.08, v2.5) the extension to 'avsi'.  See also `Q5.2`_.


**Q2.9: How do I load my clip into AviSynth (audio) ?**

A: This can be done in several ways:

1.  Using AviSource (with uncompressed WAV, CBR/VBR MP2-audio (starting
    from v2.04) or CBR/VBR MP3-audio (starting from v2.04)):

*`AviSource`_("d:\filename.avi")*

Starting from v2.05 you can extract audio from a AVI-file in this way:
*`WavSource`_("d:\filename.avi")*

2.  Use the audio decoder plugin MPASource, see `Q3.4`_ and `Q3.5`_ for
    importing mp1/mp2/mp3 audio.


3.  See `DirectShowSource`_ for downmixing AC3 audio.


4.  Put a WAV-header on your `mp2`_ or mp3 (with Besweet) audio file and
    use WavSource to import the audio.  You also need ACM codecs for `mp2`_,
    and for mp3 (Radium codec, see doom's download section).  Use WavSource
    to load the WAV:

*`WavSource`_("d:\filename.wav")*

Up to v2.07 the audio must be mono or stereo.  Starting from v2.5 you can
also import uncompressed multichannel audio.


**Q2.10: Can I import an audio file other than a WAV-file?**

A: Yes:

-   Uncompressed audio files (that is uncompressed WAV-files) can be
    loaded in all versions up to v2.03.
-   Starting from v2.04 compressed WAV-files can be loaded (currently
    only MP2/MP3-files with a WAV-header).
-   Starting from v2.5 you can also load uncompressed multichannel audio.
-   Using the MPASource and AC3filter plugins you can import mp1/mp2/mp3
    and AC3 audio.

See also `Q2.9`_.


**Q2.11: How do I join video and audio ?**

A: Make an avs-file containing the lines (change the filenames and paths):

video = `AviSource`_("d:\filename1.avi")
audio = `WavSource`_("d:\filename2.wav")
`AudioDub`_(video, audio)


**Q2.12:  I get an unrecognized exception in the line where I use
DirectShowSource?**

A: Have you got VobSub installed? Have a look at this `thread`_. Upgrade to
VobSub v2.20 or higher. If someone has an explanation, please post it in the
thread.


**S3: Filters and colorspaces:**


**Q3.1: What is RGB/YUV-colorspace ?**

A: These are two different ways to represent colors: YUV colorspace and RGB
colorspace.  In YUV colorspace there is one component that represent
lightness (luma) and two other components that represent color (chroma).  As
long as the luma is conveyed with full detail, detail in the chroma
components can be reduced by subsampling (filtering, or averaging) which can
be done in several ways (thus there are multiple formats for storing a
picture in YUV colorspace).  In RGB colorspace there are three components,
one for the amount of Red, one for the amount of Green and one for the amount
of Blue.  Also in the colorspace there are multiple formats for storing a
picture which differ in the amount of samples are used for one of the three
colors.

Information can be found here: `YUV Formats`_, `RGB Formats`_, `MSDN YUV
Formats`_ and `Chroma subsampling by Charles Poyton`_.

As of AviSynth v1.0x/v2.0x, RGB24, RGB32, and YUY2 are supported.  In
AviSynth v2.5x there is also support for YV12.


**Q3.2: In which colorspaces do AviSynth and the internal filters work ?**

A: AviSynth works in RGB and YUV using the RGB32, RGB24, YUY2 and YV12
formats.  Most of the internal filters work in any of these formats, too.
Which color format a filter requires, can be found [`here`_].


**Q3.3: How do I load a plugin in to AviSynth ?**

A: Starting from v2.05 you can use its auto-plugin loading feature. The path
of the plugin directory is set during install. But if you want to change it
for some reason, change or add the following lines:

*REGEDIT4*

*[HKEY_LOCAL_MACHINE\SOFTWARE\Avisynth]*
*"PluginDir"="c:\\program files\\avisynth 2.5\\plugins"*

Change the path above if necessary and make sure you created the plugin-dir
as well. Save it as install_autoplugin.reg, and merge it to your registry
file by right-clicking on it in your explorer. Finally move all your plugins
/script-functions into the plugin directory. If you want to load plugins
manually, use "LoadPlugin". An example script:

*LoadPlugin("d:\mpeg2dec.dll")*
*mpeg2source("d:\filename.d2v")*


**Q3.4: Where can I download external filters for AviSynth v1.0x/v2.0x ?**

A: Most of them can be found in the AviSynth section at Doom9. But below you
will find links to most of them. If you know of a plugin which is missing,
please feel free to add it to the list using the "Edit this document" link to
the left. Most of these plugins work in YUY2. If you can't find the plugin
(the attachments are still disabled), you can download the plugins at
[`WarpEnterprises`_] homepage.

**Deinterlacing & Pulldown Removal:**
*All PAL, NTSC, and SECAM video is interlaced, which means that only every
other line is broadcast at each refresh interval.  Deinterlacing filters let
you take care of any problems caused by this. IVTC (inverse telecine, aka
pulldown removal) filters undo the telecine process, which comes from
differences between the timing of your video and its original source.*

1.  `Decomb Filter package (by Donald Graft)`_: This package of plugin
    functions for AviSynth provides the means for removing combing artifacts
    from telecined progressive streams, interlaced streams, and mixtures
    thereof. Functions can be combined to implement inverse telecine for both
    NTSC and PAL streams. *[YUY2]*


2.  `ViewFields/UnViewFields (by Simon Walters)`_: ViewFields and
    UnViewFields are a complementary pair of filters to display and identify
    top and bottom fields from an interlaced source. *[YUY2]*


3.  `GreedyHMA plugin (by Tom Barry)`_: DScaler's Greedy/HM algorithm
    code to perform pulldown matching, filtering, and video deinterlacing.
    *[YUY2]*


4.  `Motion compensated deinterlace filter "TomsMoComp" (by Tom Barry)`_:
    This filter uses motion compensation and adaptive processing to
    deinterlace video source (not for NTSC film). *[YUY2]*


5.  `SmoothDeinterlacer (by Gunnar Thalin, ported to AviSynth by
    Xesdeeni)`_: A port of the VirtualDub [Smooth Deinterlacer] filter.
    *[YUY2, RGB]*


6.  IVTC plugin v2.2 (by "Wizard_FL", Dooms download section): This
    plugin reverses the telecine process. *[YUY2]*


7.  `"IT" (by thejam79)`_: Inverse telecine plugin. `Translation of
    README`_


8.  `"AntiComb" (by ?)`_: This filter remove combing (interlace
    artifacts). `Translation of README`_


9.  See also Auto24FPS and AutoDeint in the `MiscPlugins`_ section below.

**Spatio-Temporal Smoothers:**
*These filters use color similarities and differences both within and between
frames to reduce noise and improve compressed size.  They can greatly improve
noisy video, but some care should be taken with them to avoid blurred
movement and loss of detail.*

1.  `PeachSmoother (by Lindsey Dubb)`_: An adaptive smoother optimized
    for TV broadcasts: `documentation`_; `discussion`_. The Peach works by
    looking for good pixels and gathering orange smoke from them. When it has
    gathered enough orange smoke, it sprinkles that onto the bad pixels,
    making them better. Works only on computers with SSE instructions
    (Athlons, Pentium 3 or 4, recent Celerons, or later). *[YUY2]*


2.  `"MAM" (by Marc FD)`_: This filter uses movement detection to adapt
    the denoising method used, in still areas it uses temporal filtering and
    in moving areas it uses spatial filtering with any spatial and temporal
    filter you want.  It is no longer developed but it can temporarily be
    downloaded from this `site`_. *[YUY2]*


3.  `NoMoSmooth (by SansGrip)`_: A motion adaptive spatio-temporal
    smoother: `documentation`_; `discussion`_. *[YUY2]*


4.  `Dust (by Steady)`_: A noise remover. *[YUY2, RGB]*


5.  `SpatioTemporal Median Filter "STMedianFilter" (by Tom Barry)`_:
    STMedianFilter is a (slightly motion compensated) spatial/temporal median
    filter. Bug: strange color changes (clip becomes purple) *[YUY2]*


6.  `Convolution3D (by Vlad59)`_: Convolution3D is a spatio-temporal
    smoother, it applies a 3D convolution filter to all pixels of consecutive
    frames. *[YUY2]*

**Spatial Smoothers:**
*These use color similarities and differences within a frame to improve the
picture and reduce compressed size. They can smooth out noise very well, but
overly aggressive settings for them can cause a loss of detail.*

1.  `Masked Smoother "msmooth" (by Donald Graft)`_: The filter is
    effective at removing mosquito noise as well as effectively smoothing
    flat areas in (especially) anime. (currently in the repair shop) *[RGB]*


2.  `Smoother HiQ(uality) plugin (by Klaus Post)`_: This filter performs
    (spatial) smoothing on video material to eliminate noise and MPEG
    artifacts. *[YUY2]*


3.  `msoften (by Marc FD)`_: This Filter is a spatial denoiser like
    2dcleaner.  Some discussion can be found `here`_. *[YUY2]*


4.  `General convolution plugin (by Richard Berg)`_: A spatial smoother
    (`description`_). This plugin will be a built-in function starting from
    AviSynth v2.01. *[YUY2, RGB]*


5.  `Wavelet Noise Reduction (by thejam)`_: It can remove single-
    frequency noise in three different frequency bands, independently for X-
    and Y-direction and for the Y, Cr and Cb colorplane (`documentation`_).
    Note that it only works for PC's with SSE instructructions. *[YUY2]*


6.  `2D Cleaner Noise Reduction filter "_2DClenYUY2"`_ *[YUY2]*


7.  Also see KenKunNR in the `Misc Plugins`_ section, below.

**Temporal Smoothers:**
*These filters use color similarities and differences between frames to
improve the picture and reduce compressed size.  They can get rid of most
noise in stationary areas without losing detail, but overly strong settings
can cause moving areas to be blurred.*

1.  `TemporalSoften2 plugin (by Dividee)`_: This plugin is better than
    the built-in TemporalSoften up to v2.02; it removes noise from a video
    clip by selectively blending pixels.  It is built into v2.03 and all
    subsequent versions (it replaces the old function and it is called the
    same: TemporalSoften). *[YUY2]*


2.  `TemporalSmoother plugin (by Dividee)`_: This filter is an adaptive
    noise reducer, working along the time axis. *[YUY2]*


3.  `TemporalCleaner (by Jim Casaburi; ported to AviSynth by Vlad59)`_: A
    simple but very fast temporal denoiser, aimed to improve compressibility.
    *[YUY2]*


4.  `Grape Smoother (by Lindsey Dubb)`_: `documentation`_; `discussion`_;
    When colors change just a little, the filter decides that it is probably
    noise, and only slightly changes the color from the previous frame. As
    the change in color increases, the filter becomes more and more convinced
    that the change is due to motion rather than noise, and the new color
    gets more and more weight. *[YUY2]*


5.  `Chroma Noise Reducer (by Marc FD)`_: Reduces the noise on the chroma
    (UV) and preserves the luma (Y), `discussion`_. *[YUY2]*


6.  `Dynamical Noise Reduction 2 filter "DNR2"`_ *[YUY2, RGB]*


7.  Also see KenKunNRT in the `Misc Plugins`_ section, below.

**Sharpen/Soften Plugins:**
*These are closely related to the Spatial Smoothers, above.  They attempt to
improve image quality by sharpening or softening edges.*

1.  `Smart sharpening filter "MSharpen" (by Donald Graft)`_: This filter
    is very effective at sharpening important edges without amplifying noise.
    *[YUY2, RGB]*


2.  `Sharpen/Blur filter "Focus2" (by Marc FD)`_: Sharpen2 and Blur2 are
    MMX optimisations of the built in Sharpen and Blur functions.  Starting
    from v2.50 it will replace the Sharpen and Blur functions. *[YUY2, RGB]*


3.  `Unfilter plugin (by Tom Barry)`_: This filter softens/sharpens a
    clip: `discussion`_.  It implements horizontal and vertical filters
    designed to (slightly) reverse previous efforts at softening or edge
    enhancment that are common (but ugly) in DVD mastering. *[YUY2]*


4.  See also WarpSharp, Xsharpen, and Unsharp Mask in the `Misc Plugins`_
    section, below.

**Resizers:**

1.  `Lanczos resize filter (Implemented by Nic)`_: Starting from v2.06
    AviSynth will have faster a built-in lanczos3 resizer. *[YUY2, RGB]*


2.  `SimpleResize plugin (by Tom Barry)`_: Very simple and fast two tap
    linear interpolation.  It is unfiltered which means it will not soften
    much. *[YUY2]*

**Subtitles:**

1.  `VobSub plugin (by Gabest)`_: A plugin for importing your subtitles.
    *[YUY2, RGB]*

**MPEG Decoder (source) Plugins:**

1.  `"MPEG2DEC" (by dividee):`_ Mpeg2dec is a plugin which enables
    AviSynth to import MPEG2 files.


2.  `"MPEG2DEC2" (by Tom Barry)`_: A MPEG2DEC.DLL substitute.  It is the
    same MPEG2DEC.DLL with SSE2 optimization. Faster with Pentium IV CPU.


3.  `"MPEG2DEC3" (by Marc FD)`_: A MPEG2DEC.DLL modification with
    deblocking and deringing, `discussion`_.


4.  `"MpegDecoder" (by Nic)`_: A MPEG2DEC.DLL substitute.  Can also read
    MPEG-2 Transport Streams (VOB) and works very quickly.

**MPA Decoder (source) Plugins:**

1.  `MPASource (by Warpenterprises)`_: A mp1/mp2/mp3 audio decoder
    plugin, `discussion`_.

**Broadcast Video Plugins:**
*These are meant to take care of various problems which show up when over the
air video is captured.  Some help with luma/chroma separation, others reduce
interference problems or compensate for overscan.*

1.  `AntiBlink (by Kurosu)`_: Tries to diminish shimmering (rainbow
    effects) in areas with sharp changes in luminance (for instance,
    letters). *[YUY2]*


2.  `Guava Comb (by Lindsey Dubb)`_: This is a comb filter, meant to get
    rid of rainbows, dot crawl, and shimmering in stationary parts of an
    image. `documentation`_; `discussion`_* [YUY2]*


3.  `Ghostbuster (by SansGrip)`_: This filter removes "ghosts" from a
    clip.  A ghost in this context is a faint copy of the picture offset
    horizontally.  It works by either subtracting or adding the image from
    itself at the specified offset.  This filter is based on Krzysztof
    Wojdon's `Exorcist`_ VirtualDub filter. *[YUY2]*


4.  `BorderControl plugin (by Simon Walters)`_: After capturing video you
    might want to crop your video to get rid of rubbish.  BorderControl
    enables you to smear added borders instead of adding solid borders
    preventing artefacts between picture and border. *[YUY2]*


5.  `AutoCrop plugin (by CropsyX)`_: Automatically crops black borders
    from a clip. `discussion`_* [YUY2]*

**Misc Plugins:**

1.  `ImageSequence plugin (by Bzzz2)`_: A plugin that lets you open image
    sequences.


2.  `Robust duplicate frame detector "Dub" (by Donald Graft)`_: This
    filter reduces the size of anime movies by "removing" duplicated frames.
    *[YUY2]*


3.  `Tweak plugin (by Donald Graft)`_: Adjusts hue, saturation,
    brightness, and contrast.  This is a built in function starting with
    AviSynth v2.01. *[YUY2]*


4.  `WarpSharp, Xsharpen, UnsharpMask, KenKunNR, KenKunNRT, UVTimingH,
    UVTimingV, LoadAviUtlInputPlugin, LoadAviUtlFilterPlugin,
    ConvertYUY2ToAviUtlYC, ConvertAviUtlYCToYUY2, EraseGhost, SearchGhost,
    EraseGhostV, SearchGhostV, Auto24FPS, AutoDeint, FrameCache,
    AVIEncodeVideo, LoadPlugin (by ???)`_: Ported VirtualDub filters and
    AviUtl filters. Last version can be found `here`_. *[YUY2]*


5.  `AviSynth monitor "avsmon" (by johann.Langhofer)`_: This plugin
    enables you to preview the video during the conversion and to determine
    the exact audio delay.* [YUY2, RGB ?]*


6.  `MergeLuma/MergeChroma plugin (by Klaus Post)`_: This plugin is a
    built in function starting with AviSynth v2.01. *[YUY2]*


7.  `Call (by Nic)`_: A plugin which enables you to call and pass
    parameters to a external commandline program like Besweet.


8.  `Blockbuster (by SansGrip)`_: With this filter one can use several
    methods to reduce or eliminate DCT blocks: adding noise (Gaussian
    distributed), sharpening, or blurring.  Some discussion can be found
    `here`_. *[YUY2, RGB ?]*


9.  `ChromaShift (by Simon Walters)`_: ChromaShift shifts the chrominance
    information to the right by two pixels to compensate for incorrect Y/UV
    registration. *[YUY2]*


10. `TurnLeft and TurnRight (by Warpenterprises)`_: Rotates your clip -90
    or 90 degrees.  This plugin will is a built in function starting with
    AviSynth v2.51.* [RGB]*


11. `Chr.dll (by WarpEnterprises)`_: Let's you add ASCII CHaRacters and
    starting time.


12. `Spray (by WarpEnterprises)`_: It takes pixels from "nearby" and
    sprays them around, so you can spray pixel from outside the logo area
    randomly inside. *[RGB32]*


13. `Zoom "Pan/Zoom/Rotate" (by WarpEnterprises)`_: A plugin for
    Pan/Zoom/Rotate your clip. *[RGB32]*


14. `MJPEGcorrect plugin`_: Luma (brightness) in MJPEG decoders is often
    decoded incorrectly to the YUV luma-range.  This is a special purpose
    plugin written to fix this issue with MJPEG videos, `description`_.
    *[YUY2]*


15. Many VirtualDub filters, see section `S4: Importing filters from
    VirtualDub`_. *[RGB32]*



**Q3.5: Where can I download external filters for AviSynth v2.5x ?**

A: Most of them can be found in the AviSynth section at Doom9. But below you
will find links to most of them. If you know of a plugin which is missing,
please feel free to add it to the list using the "Edit this document" link to
the left. Most of these plugins work in YUY2. If you can't find the plugin
(the attachments are still disable), you can download the plugins at
[`WarpEnterprises`_] homepage.

**Deinterlacing & Pulldown Removal:**
*All PAL, NTSC, and SECAM video is interlaced, which means that only every
other line is broadcast at each refresh interval.  Deinterlacing filters let
you take care of any problems caused by this. IVTC (inverse telecine, aka
pulldown removal) filters undo the telecine process, which comes from
differences between the timing of your video and its original source.*

1.  `rePal (by Bach)`_: A usefull plugin for doing a 30->25 IVTC
    conversion. It must be used in conjunction with a (smart)bob. It can be
    used when your source is PAL telecined material. *[YV12, YUY2]*


2.  `Unblend (by Bach)`_: A plugin based on Warpenterprise's deblend
    algorithm and Neuron2's decimate code. It's for messed up NTSC->PAL
    conversions.* [YV12]*


3.  `Decomb Filter package (by Donald Graft)`_: This package of plugin
    functions for AviSynth provides the means for removing combing artifacts
    from telecined progressive streams, interlaced streams, and mixtures
    thereof. Functions can be combined to implement inverse telecine for both
    NTSC and PAL streams. `discussion`_*[YV12, YUY2]*


4.  `Area based deinterlacer (by Donald Graft)`_: Port of the Virtuldub
    filter. *[RGB32]*


5.  `DGBob (by Donald Graft)`_: This filter splits each field of the
    source into its own frame and then adaptively creates the missing lines
    either by interpolating the current field or by using the previous
    field's data. `discussion`_* [YV12, YUY2, RGB]*


6.  `KernelDeint (by Donald Graft)`_: This filter deinterlaces using a
    kernel approach. It gives greatly improved vertical resolution in
    deinterlaced areas compared to simple field discarding. [`discussion`_].
    *[YV12, YUY2, RGB]*


7.  `MultiDecimate (by Donald Graft)`_: Removes N out of every M frames,
    taking the frames most similar to their predecessors. `discussion`_*
    [YUY2]*


8.  `Smoothdeinterlacer (recompiled by Donald Graft)`_: A port of the
    VirtualDub Smooth Deinterlacer filter. *[YUY2, RGB32]*


9.  `Interpolation Bob (by kevina20723)`_: This filter works identically
    to the AviSynth built-in Bob filter except that it uses linear
    interpolation instead of bicubic resizing (C-plugin). *[YV12, YUY2]*


10. `SmartDecimate (by kevina20723)`_: It should be very good at handling
    irregular telecines, and will also handle hybrid clips fairly well
    without any excessive jerkiness or blurring (C-plugin). [`discussion`_].
    *[YV12, YUY2]*


11. `TPRIVTC (by Kurosu)`_: It uses the IVTC information from Tsunami
    MPEG Encoder Project Files.* [YV12, YUY2]*


12. `Progressive Frame Restorer "PFR" (by Simon Walters)`_: Recover
    original progressive film frames that have undergone the telecine to NTSC
    30fps to PAL 25fps process whilst trying to maintain correct temporal
    field order. [`discussion`_]. *[YV12, YUY2]*


13. `"IT" (by thejam79, recompiled by Donald Graft)`_: Inverse telecine
    plugin. `Translation of README`_.* [YUY2]*


14. `GreedyHMA (by Tom Barry)`_: DScaler's Greedy/HM algorithm code to
    perform pulldown matching, filtering, and video deinterlacing.
    `discussion`_*[YUY2]*


15. `Motion compensated deinterlace filter "TomsMoComp" (by Tom Barry)`_:
    This filter uses motion compensation and adaptive processing to
    deinterlace video source (not for NTSC film). `discussion`_* [YV12,
    YUY2]*


16. `UnComb IVTC (by Tom Barry)`_: Filter for matching up even and odd
    fields of properly telecined NTSC or PAL film source video.
    `discussion`_* [YV12]*


17. See also Auto24FPS and AutoDeint in the `MiscPlugins`_ section below.

**Spatio-Temporal Smoothers:**
*These filters use color similarities and differences both within and between
frames to reduce noise and improve compressed size.  They can greatly improve
noisy video, but some care should be taken with them to avoid blurred
movement and loss of detail.*

1.  `PeachSmoother (by Lindsey Dubb)`_: An adaptive smoother optimized
    for TV broadcasts: [`documentation`_], [`discussion`_]. The Peach works
    by looking for good pixels and gathering orange smoke from them. When it
    has gathered enough orange smoke, it sprinkles that onto the bad pixels,
    making them better. Works only on computers with SSE instructions
    (Athlons, Pentium 3 or 4, recent Celerons, or later). *[YUY2]*


2.  `FluxSmooth (by SansGrip)`_: spatio-temporal smoother,
    `discussion`_*. [YV12]*


3.  `MipSmooth filter (by Sh0dan)`_: It takes the source frame, and
    creates three new versions, each half the size of the previous. They are
    scaled back to original size. They are compared to the original, and if
    the difference is below the threshold, the information is used to form
    the final pixel. *[YV12]*


4.  `SpatioTemporal Median Filter "STMedianFilter" (by Tom Barry)`_:
    STMedianFilter is a (slightly motion compensated) spatial/temporal median
    filter.* [YV12, YUY2]*


5.  `Convolution3DYV12 (by Vlad59)`_: Convolution3D is a spatio-temporal
    smoother, it applies a 3D convolution filter to all pixels of consecutive
    frames. `discussion`_* [YV12]*

**Spatial Smoothers:**
*These use color similarities and differences within a frame to improve the
picture and reduce compressed size. They can smooth out noise very well, but
overly aggressive settings for them can cause a loss of detail.*

1.  `Masked Smoother "MSmooth" (by Donald Graft)`_: This filter is
    effective at removing mosquito noise as well as effectively smoothing
    flat areas in anime. `discussion`_* [YV12, RGB32]*


2.  `SmoothUV (by Kurosu)`_: This filter can be used to reduce rainbows,
    as done by SmartSmoothIQ. [`discussion`_]. *[YV12]*


3.  `VagueDenoiser (by Lefungus)`_: A simple denoiser that uses wavelets.
    *[YV12]*


4.  `Deen (by Marc FD)`_: Several denoisers. [`discussion`_] This filter
    can cause memory leaks, so use at your own risk. *[YV12]*


5.  `eDeen (by Marc FD)`_: Spatial monster. This filter can cause memory
    leaks, so use at your own risk.* [YV12]*


6.  `SmoothHiQ (recompiled by Richard)`_: *[YUY2]*


7.  `2D Cleaner Noise Reduction filter "_2DClenYUY2"`_ *[YUY2]*


8.  Also see KenKunNR in the `Misc Plugins`_ section, below.

**Temporal Smoothers:**
*These filters use color similarities and differences between frames to
improve the picture and reduce compressed size.  They can get rid of most
noise in stationary areas without losing detail, but overly strong settings
can cause moving areas to be blurred.*

1.  `TemporalCleaner (by Jim Casaburi; ported to AviSynth by Vlad59)`_: A
    simple but very fast temporal denoiser, aimed to improve compressibility.
    *[YV12]*


2.  `Grape Smoother (by Lindsey Dubb)`_: [`documentation`_],
    [`discussion`_]. When colors change just a little, the filter decides
    that it is probably noise, and only slightly changes the color from the
    previous frame. As the change in color increases, the filter becomes more
    and more convinced that the change is due to motion rather than noise,
    and the new color gets more and more weight. *[YUY2]*


3.  `atc (by Marc FD)`_: Temporal cleaner.* [YV12]*


4.  `Chroma Noise Reducer "Cnr2" (by Marc FD)`_: Reduces the noise on the
    chroma (UV) and preserves the luma (Y), [`discussion`_] *[YV12, YUY2]*


5.  `Dynamical Noise Reduction 2 filter "DNR2"`_ *[YV12]*


6.  Also see KenKunNRT in the `Misc Plugins`_ section, below.

**Sharpen/Soften Plugins:**
*These are closely related to the Spatial Smoothers, above.  They attempt to
improve image quality by sharpening or softening edges.*

1.  `MSharpen (by Donald Graft)`_: This plugin for Avisynth implements an
    unusual concept in spatial sharpening. Although designed specifically for
    anime, it also works quite well on normal video. The filter is very
    effective at sharpening important edges without amplifying noise.
    `discussion`_*[YV12, YUY2, RGB]*


2.  `asharp (by MarcFD)`_: adaptive sharpening filter, [`discussion`_]
    *[YV12]*


3.  `Unfilter plugin (by Tom Barry)`_: This filter softens/sharpens a
    clip.  It implements horizontal and vertical filters designed to
    (slightly) reverse previous efforts at softening or edge enhancment that
    are common (but ugly) in DVD mastering. [`discussion`_]* [YV12, YUY2]*


4.  See also WarpSharp, Xsharpen, and Unsharp Mask in the `Misc Plugins`_
    section, below.

**Resizers:**

1.  `bicublinresize (by Marc FD)`_: This is a set of resamplers:
    FastBilinear (similar to tbarry's simpleresize), FastBicubic (an
    unfiltered Bicubic resampler) and Bicublin (uses bicubic on Y plane and
    bilinear on UV planes). `discussion`_. *[YV12]*


2.  `ReduceBy2 replacement for TMPGEnc (by scmccarthy)`_: This filter is
    only useful as a replacement for ReduceBy for users who need to convert
    to the RGB color space anyway. It avoids the interpolation of the chroma
    planes needed to convert to RGB by resizing the luma plane instead.
    *[RGB]*


3.  `SimpleResize (by Tom Barry)`_: Very simple and fast two tap linear
    interpolation.  It is unfiltered which means it will not soften much.
    *[YV12, YUY2]*


4.  `YV12InterlacedReduceBy2 (by Tom Barry)`_: InterlacedReduceBy2 is a
    fast Reduce By 2 filter, usefull as a very fast downsize of an interlaced
    clip. [`discussion`_]* [YV12]*

**Subtitles:**

1.  `VSFilter (by Gabest)`_: For the subtitle fans! [`discussion`_]

**MPEG Decoder (source) Plugins:**

1.  `MPEG2DEC (by dividee)`_ Mpeg2dec is a plugin which lets AviSynth
    import MPEG2 files. (outputs to YUY2)


2.  `MPEG2DEC3 (by Marc FD and others)`_: A MPEG2DEC.DLL modification
    with deblocking and deringing. Note that the colorspace information of
    dvd2avi is ignored when using mpeg2dec.


3.  `Mpegdecoder (by Nic)`_: This DLL lets you load VOB/MPEG-2/MPEG-1
    files to be loaded directly into AviSynth. `discussion`_.

**MPA Decoder (source) Plugins:**

1.  `evilMPASource (by Nic)`_: MPASource with MPEG1/2 input support.


2.  `MPASource (by Warpenterprises)`_: A mp1/mp2/mp3 audio decoder
    plugin, `discussion`_.

**Plugins to compare video quality using specific video quality metrics:**

1.  `SSIM (by Lefungus)`_: Filter to compare video quality (similar as
    psnr, but using a different video quality metric). *[YV12]*


2.  `VqmCalc (by Lefungus)`_: Filter to compare video quality (similar as
    psnr, but using a different video quality metric). *[YV12]*

**Broadcast Video Plugins:**
*These are meant to take care of various problems which show up when over the
air video is captured.  Some help with luma/chroma separation; Others reduce
interference problems or compensate for overscan.*

1.  `Super8Equal (by Belgabor)`_: One problem of the transfer of Super8
    films to digital media is the inhomogenous brightness produced by
    projectors. Usually the brighness drops in a circular fashion from the
    center to the rim. This filter was written to counteract this problem.
    *[YV12, YUY2, RGB]*


2.  `AutoCrop plugin (by CropsyX)`_: Automatically crops black borders
    from a clip. `discussion`_. *[YV12, YUY2]*


3.  `Declick (by Donald Graft)`_: Removes light horizontal clicks.
    *[YUY2]*


4.  `Deflicker filter (by Donald Graft, port of the VirtualDub filter)`_:
    This filter corrects video that has frame luminance variations over time,
    what we might generically call flickering. *[YUY2]*


5.  `Conditional Temporal Median Filter (by kevina20723)`_: Removes
    temporal noise in the form of small dots and streaks (C-plugin). *[YV12]*


6.  `X-Logo (by Leuf)`_: A filter to remove logos. (Note there's an
    internal conversion to RGB32 and back.) *[YV12, YUY2, RGB]*


7.  `Guava Comb (by Lindsey Dubb)`_: This is a comb filter, meant to get
    rid of rainbows, dot crawl, and shimmering in stationary parts of an
    image. [`documentation`_], [`discussion`_]. *[YUY2]*


8.  `FixVHSOversharp (by MrTibs)`_: Repairs the light and dark halos that
    follow high contrast edges found in VHS sources. [`discussion`_].
    *[YUY2]*


9.  `BorderControl (by Simon Walters)`_: After capturing video you might
    want to crop your video to get rid of rubbish.  BorderControl enables you
    to smear added borders instead of adding solid borders preventing
    artefacts between picture and border. *[YV12, YUY2]*


10. `FillMargins (by Tom Barry)`_: A similar filter as BorderControl.
    [`discussion`_] *[YV12]*


11. `Reinterpolate411 (by Tom Barry)`_: It seems that even chroma pixels
    are just being duplicated in the MainConcept codec (NTSC). The new filter
    will help that by discarding the odd chroma pixels and recreating them as
    the average of the 2 adjacent even pixels. [`discussion`_]. *[YUY2]*

**Misc Plugins:**

1.  `Imagesequence plugin (by Bzzz, modified by Warpenterprises and
    Sh0dan)`_: Let's you import image sequences like .TIF, .TGA and .JPG
    files (images need to be 24 or 32 bits per pixel). This plugin is built
    in starting from AviSynth v2.52, and it is called `ImageReader`_.


2.  `Dup (by Donald Graft)`_: This is intended for use in clips that have
    a significant number of duplicate content frames, but which differ due to
    noise. Typically anime has many such duplicates. By replacing noisy
    duplicates with exact duplicates, a bitrate reduction can be achieved.
    `discussion`_* [YV12, YUY2]*


3.  `Convert3d (by hanfrunz)`_: Converts interlaced 3D Movies (one field
    left, other field right picture) to anaglyph (red/cyan) format using
    photoshops "screen"-blend method. *[YUY2, RGB]*


4.  `AviSynth monitor "avsmon" (by johann.Langhofer)`_: This plugin
    enables you to preview the video during the conversion and to determine
    the exact audio delay.* [YV12, YUY2 ?, RGB ?]*


5.  `AVISynth C API (by kevina20723)`_: C-plugins must be loaded with
    LoadCPlugin using AviSynth v2.52 or older versions, and can also be
    loaded with LoadPlugin starting from AviSynth v2.53. Advice: keep this
    plugin outside your auto plugin loading directory to prevent crashes.
    [`discussion`_].


6.  `MaskTools (by Kurosu)`_: Some general mask tools. *[YV12]*


7.  `Call (by Nic)`_: A plugin which enables you to call and pass
    parameters to an external commandline program like Besweet.


8.  `AudioGraph (by Richard Ling, modified by Sh0dan)`_: Displays the
    audio waveform on top of the video. *[YUY2, RGB]*


9.  `Blockbuster (by Sansgrip, recompiled by CruNcher)`_: With this
    filter one can use several methods to reduce or eliminate DCT blocks:
    adding noise (Gaussian distributed), sharpening, or blurring. *[YUY2]*


10. `ReverseFieldDominance (by Sansgrip)`_: Reverses the field dominance
    of PAL DV. `discussion`_. *[YUY2, RGB]*


11. `ChromaShift (by Simon Walters)`_: ChromaShift shifts the chrominance
    information in any direction, to compensate for incorrect Y/UV
    registration. *[YUY2]*


12. `CompareYV12 (by Shalcker)`_: YV12 version of the internal filter
    "Compare". [`discussion`_]. *[YV12]*


13. `SelectByString (by stickboy)`_: This filter can be used to create
    wrapper functions to specify presets to other filters (C-plugin). *[YV12,
    YUY2, RGB]*


14. `AddGrain (by Tom Barry)`_: AddGrain generates film like grain or
    other effects (like rain) by adding random noise to a video clip. This
    noise may optionally be horizontally or vertically correlated to cause
    streaking. *[YV12]*


15. `BT709ToBT601 (by Tom Barry)`_: Converts HDTV (BT.709) to SDTV
    (BT.601) color space. [`discussion`_] *[YV12]*


16. `DctFilter (by Tom Barry)`_: Reduces high frequency noise components
    using Discrete Cosine Transform and its inverse.  Results in a high
    compressibility gain, when it is used at the end of your script.
    Height/width must be a multiple of 16. `discussion`_. *[YV12, YUY2]*


17. `FrameDbl (by Tom Barry)`_: A motion compensated frame doubler, made
    from STMedianFilter. [`discussion`_] *[YV12]*


18. `Undot (by Tom Barry)`_: UnDot is a simple median filter for removing
    dots, that is stray orphan pixels and mosquito noise.  It basicly just
    clips each pixel value to stay within min and max of its eight
    surrounding neigbors. [`discussion`_]. *[YV12, YUY2]*


19. `Chr (by WarpEnterprises)`_: Let's you add ASCII CHaRacters and
    starting time. This plugin will be a built-in function starting from
    v2.52.


20. `DVinfo (by WarpEnterprises)`_: This filter grabs the timestamp and
    recording date info out of a DV-AVI. It should work with Type-1 and
    Type-2, standard AVI and openDML.


21. `Zoom "Pan/Zoom/Rotate" (by WarpEnterprises)`_: A plugin for
    Pan/Zoom/Rotate your clip. *[RGB32]*


22. `WarpSharp, Xsharpen, UnsharpMask, KenKunNR, KenKunNRT, UVTimingH,
    UVTimingV, LoadAviUtlInputPlugin, LoadAviUtlFilterPlugin,
    ConvertYUY2ToAviUtlYC, ConvertAviUtlYCToYUY2, EraseGhost, SearchGhost,
    EraseGhostV, SearchGhostV, Auto24FPS, AutoDeint, FrameCache,
    AVIEncodeVideo, LoadPluginEx (by our Japanese friend)`_: Ported
    VirtualDub filters and AviUtl filters. Some documentation can be found
    [`here`_]. You need to copy the [`msvcp71.dll/msvcr71.dll`_] (Microsoft C
    Runtime Library, v7) to your windows system directory. *[YV12, YUY2]*


**Q3.6: Where can I download utilities for AviSynth ?**

A: Several utilities are available:

-   `AvsCompare (by TheWEF and aquaplaning)`_: This is a little tool to
    compare video material and/or the effect of choosen AviSynth filters.
    [`discussion`_]
-   `AvsTimer (by kassandro)`_: A small filter with virtually no
    overhead, which allows one to measure the performance of plugins or
    groups of plugins.
-   `AVISynth BatchScripting`_: A little Batch file for creating fastly
    "AVS AviSynth Script files". With available presets: 1:1-VGA to VCD, DVB
    /DVD-PAL to 1:1-VGA and DVB/DVD-PAL to VCD. (Batches runs under
    WinNT/2000/XP only)


**Q3.7: How do I convert between the colorspaces ?**

A: If you are using mpeg2dec3 (the appropriate one for AviSynth v2.5x) you
can also use the conversions available in this dll (for example when you want
to convert to RGB24).  Using AviSynth itself:

*converting to YV12:*
`ConvertToYV12`_

*converting to YUY2:*
`ConvertToYUY2`_

*converting to RGB:*
`ConvertToRGB`_

Note that converting between colorspaces isn't completely lossless, and doing
several conversions back and forth may degrade your signal.  The first
conversion back and forth does not hurt your source, but if you use three or
more, it may.  Starting with version v2.03, there is a `ConvertBackToYUY2`_
which offers better symmetry if your RGB source was previously converted from
YUY2.


**Q3.8: What/when do I care when filter X works in RGB- or YUV-space ?**

A: The main reason why you should care is the improvement in speed you can
obtain by not unnecessarily changing between colorspaces.  If your source is
YV12 (when encoding DVD's for example, or captures from digital sources) try
to use only filters/plugins which work with YV12 input.  On the other hand if
your source is in RGB (for example from analog captures) try to use only
filters/plugins which work in RGB-space.

Speed is also quite different between the different colorspaces, because each
colorspace takes up different amounts of memory.  The slowest colorspace is
usually RGB24, because every pixel has an odd alignment in memory, avoid
using this mode.  The fastest mode is usually YV12 (followed by YUY2),
because data takes less than half as much space as RGB32.  So if you have to
process your video a lot, try using ConvertToYV12 or `ConvertToYUY2`_ before
you do your filtering.  Note that `ConvertToRGB`_ converts to RGB32 if the
source is YV12/YUY2 - use `ConvertToRGB32`_ to force a RGB24 to RGB32
conversion.

You should also consider your destination colorspace.  If you plan on
converting to DivX/XviD/Huffyuv in VirtualDub without applying filters in
VirtualDub, "Fast Recompress" will deliver the YUY2-data (or YV12 data if you
use VirtualdubMod) directly to the codec, saving you another colorspace
conversion.  On the other hand, if you plan using TMPGEnc or VirtualDub in
"Full Processing" mode, you may consider delivering the source as RGB.


**Q3.9: How do I use and where can I get the "Subtitler" and "BMP Loader"
plugins ?**

A: These dll files are created by DVD2SVCD and only DVD2SVCD is using them.
But you can also use them in AviSynth. Have a look in this [`thread`_].


**S4: Importing filters from VirtualDub:**


**Q4.1: Where can I download the latest version of scripts which import
filters from VirtualDub ?**

A: The AviSynth scripts are on the `ShareFunctions`_ page, or you can
download a package called vdub_filtersv15.zip from
`http://forum.doom9.org/showthread.php?s=&threadid=23804`_ or
`http://neuron2.net/hosted.html`_


**Q4.2: Which filters are imported ?**

A: Most filters.  Read the corresponding documentation available in the zip-
file.


**Q4.3: Do these scripts work in RGB-space or in YUV-space ?**

A: Only in RGB-space (RGB32).


**Q4.4: How do I make such a script ?**

A: Example script (this VirtualDub filter can be downloaded from `Donald's
homepage`_):

Smart Bob by Donald Graft:

function VD_SmartBob(clip *clip*, bool "*show_motion*", int "*threshold*",
bool "*motion_map_denoising*")
  LoadVirtualdubPlugin("d:\bob.vdf", "_VD_SmartBob", 1)
  return clip.`SeparateFields`_._VD_SmartBob(clip.`GetParity`_?1:0,
    \  default(show_motion, false)?1:0, default(threshold, 10),
    \  default(motion_map_denoising, true)?1:0)
}

The VirtualDub plugin is imported with the command "LoadVirtualdubPlugin".
The first argument gives the path of the plugin, the second argument the name
for the plugin that will be used in the script and the third argument is
called the preroll.

The preroll should be set to at least the number of frames the filter needs
to pre-process to fill its buffers and/or updates its internal variables.
This last argument is used in some filters like: SmartBob, SmartDeinterlace,
TemporalCleaner and others.  The reason is that due to filtering architecture
of Virtual Dub the future frames can't be accessed by a filter.  Dividee
reports: "In the "Add filter" dialog of VirtualDub, some filters have a
"Lag:" value in their description. I think this is the value that must be
used as preroll.  Unfortunately, this indication is not always present.  In
those cases you have to guess."  Of course you can always ask the creator of
the filter.

The first step is to find out the sequence of the arguments in the last line
where the clip is returned.  Configure the script in VirtualDub and select
"Save processing Settings" in the File Menu or press Ctrl+S.  Open the
created .vcf file with a text editor and you should see lines like this:

VirtualDub.video.filters.Add("smart bob (1.1 beta 2)");
VirtualDub.video.filters.instance[0].Config(1, 0, 10, 1);

The order of the arguments is the one that has to be used in AviSynth.  To
find the role of the arguments, play with them in VirtualDub and examine the
resulting lines.

The second step is to test the filter and to compare it with the VirtualDub
filter itself.  For the programming itself you can learn a lot by looking at
the script which are already contained in vdub_filters.avs.

Example script which uses the function VD_SmartBob:

Import("d:\vdub_filters.avs")
`AviSource`_("d:\filename.avi")
`ConvertToRGB32`_  # only when necessary (but doesn't hurt)
VD_SmartBob(1, 0, 10, 1)
`ConvertBackToYUY2`_  # only when necessary

$Date: 2008/07/09 19:35:37 $

.. _here: faq_sections.htm
.. _http://www.avisynth.org: http://www.avisynth.org
.. _S1: About AviSynth: #s1
.. _S2: AviSynth and frameserving: #s2
.. _S3: Filters, plugins and colorspaces: #s3
.. _S4: Importing filters from VirtualDub: #s4
.. _Q1.1: What is AviSynth ?: #q1.1
.. _Q1.2: Who is developing AviSynth ?: #q1.2
.. _Q1.3: Where can I download the latest versions of AviSynth ?: #q1.3
.. _Q1.4: What are the main bugs in these versions ?: #q1.4
.. _Q1.5: Where can I find documentation about AviSynth ?: #q1.5
.. _Q1.6: How do I install/uninstall AviSynth ?: #q1.6
.. _Q1.7: Is there any difference between v1.0x, v2.0x or v2.5x ?: #q1.7
.. _Q1.8: Are plugins compiled for v2.5x compatible with v1.0x/v2.0x and
    vice versa ?: #q1.8
.. _Q1.9: Which encoding programs support YV12 ?: #q1.9
.. _Q1.10: How do I use v2.5x if the encoding programs can't handle YV12
    (like Virtualdub, TMPGEnc or CCE SP) ?: #q1.10
.. _Q1.11: How do I use with AviSynth v2.5 with Gordian Knot?: #q1.11
.. _Q1.12: What are the main advantages of processing/encoding in YV12 ?:
    #q1.12
.. _Q1.13: Is there a command line utility for encoding to DivX/XviD
    using AviSynth ?: #q1.13
.. _Q1.14: Where can I find VCF2AVS ?: #q1.14
.. _Q1.15: How do I use a plugin compiled for v2.0x in v2.5x ?: #q1.15
.. _Q1.16: How do I switch between differents Avisynth versions without
    re-install ?: #q1.16
.. _Q1.17: How do I make an AVS-file ?: #q1.17
.. _Q1.18: Where do I save my AVS-file ?: #q1.18
.. _Q1.19: How do I know which version number of AviSynth I have ?:
    #q1.19
.. _Q1.20: Does AviSynth have a GUI (graphical user interface) ?: #q1.20
.. _Q1.21: I got the message "LoadPlugin: unable to load "xxx" is not an
    AviSynth 1.0/AviSynth 2.5 plugin ?: #q1.21
.. _Q1.22: How do I know which colorspace I'm using at a given place in
    my script ?: #q1.22
.. _Q1.23: I installed AviSynth v2.5 and DivX5 (or one of the latest Xvid
    builds of Koepi), all I got is a black screen when opening my avs in
    Virtualdub/VirtualdubMod/CCE/TMPGEnc ?: #q1.23
.. _Q1.24: My computer seems to crash at random during a second pass in
    any encoder ?: #q1.24
.. _Q1.25: VirtualdubMod, WMP6.4, CCE and other programs crash every time
    on exit (when previewing an avs file) ?: #q1.25
.. _Q1.26: Are there any lossless YV12 codecs, which I can use for
    capturing for example?: #q1.26
.. _Q2.1: What is frameserving and what is it good for ?: #q2.1
.. _Q2.2: How do I use AviSynth as a frameserver ?: #q2.2
.. _Q2.3: How do I frameserve my AVS-file to encoder/application X ?:
    #q2.3
.. _Q2.4: Problems when Encoder X reads AVS-files ?: #q2.4
.. _Q2.5: How do I frameserve from Premiere/Ulead/Vegas to AviSynth ?:
    #q2.5
.. _Q2.6: When frameserving I got the following message: "Script error,
    there is no function named "xxx (the name of some filter)"" ?: #q2.6
.. _Q2.7: I get an unrecognized exception error trying to load an avs
    file with VirtualDub, using dvd2avi v1.77.3 ?: #q2.7
.. _Q2.8: How do I load my clip into AviSynth (video) ?: #q2.8
.. _Q2.9: How do I load my clip into AviSynth (audio) ?: #q2.9
.. _Q2.10: Can I import an audio file other than a WAV-file?: #q2.10
.. _Q2.11: How do I join video and audio ?: #q2.11
.. _ I get an unrecognized exception in the line where I use
    DirectShowSource?: #q2.12
.. _Q3.1: What is RGB/YUV-colorspace ?: #q3.1
.. _Q3.2: In which colorspaces do AviSynth and the internal filters work
    ?: #q3.2
.. _Q3.3: How do I load a plugin in to AviSynth ?: #q3.3
.. _Q3.4: Where can I download external filters for AviSynth v1.0x/v2.0x
    ?: #q3.4
.. _Q3.5: Where can I download external filters for AviSynth v2.5x ?:
    #q3.5
.. _Q3.6: Where can I download utilities for AviSynth ?: #q3.6
.. _Q3.7: How do I convert between the colorspaces ?: #q3.7
.. _Q3.8: What/when do I care when filter X works in RGB- or YUV-space ?:
    #q3.8
.. _Q3.9: How do I use and where can I get the "Subtitler" and "BMP
    Loader" plugins ?: #q3.9
.. _Q4.1: Where can I download the latest version of scripts which import
    filters from VirtualDub ?: #q4.1
.. _Q4.2: Which filters are imported ?: #q4.2
.. _Q4.3: Do these scripts work in RGB-space or in YUV-space ?: #q4.3
.. _Q4.4: How do I make such a script ?: #q4.4
.. _ Lukes homepage: http://neuron2.net/LVG/avisynth.html
.. _http://math.berkeley.edu/~benrg/avisynth.html:
    http://math.berkeley.edu/~benrg/avisynth.html
.. _http://www.videotools.net/uk/download.php:
    http://www.videotools.net/uk/download.php
.. _v1.0b7a by Divine:
    http://forum.doom9.org/showthread.php?s=&threadid=18243
.. _second revision (v2.0x): http://sourceforge.net/projects/avisynth2/
.. _first sourceforge project: http://sourceforge.net/projects/avisynth/
.. _here: http://cultact-server.novi.dk/kpo/avisynth/avs_cvs.html
.. _Authors.avs: ../../Examples/Authors.avs
.. _memberlist:
    http://sourceforge.net/project/memberlist.php?group_id=57023
.. _sourceforge page.:
    http://sourceforge.net/project/showfiles.php?group_id=57023
.. _Dissolve: corefilters/dissolve.htm
.. _Layer: corefilters/layer.htm
.. _MergeChroma: corefilters/merge.htm
.. _Loop: corefilters/loop.htm
.. _SegmentedAviSource: corefilters/segmentedsource.htm
.. _AviSynthTwoFiveZeroBugs:
    http://www.avisynth.org/index.php?page=AviSynthTwoFiveZeroBugs
.. _AviSynthTwoFiveOneBugs:
    http://www.avisynth.org/index.php?page=AviSynthTwoFiveOneBugs
.. _AviSynthTwoFiveTwoBugs:
    http://www.avisynth.org/index.php?page=AviSynthTwoFiveTwoBugs
.. _http://www.avisynth.org/: http://www.avisynth.org/
.. _filters: corefilters.htm
.. _this page: syntax.htm
.. _here: http://sourceforge.net/projects/virtualdubmod
.. _ConvertToYUY2: corefilters/convert.htm
.. _XviD-04112002-1 or newer: http://roeder.goe.net/~koepi/xvid.shtml
.. _crashes: http://www.divx-digest.com/software/divxcodec4.html
.. _prerelease: http://sourceforge.net/project/showfiles.php?group_id=658
    89&release_id=130443
.. _AVS2AVI: http://forum.doom9.org/showthread.php?s=&threadid=36768
.. _here: http://forum.doom9.org/showthread.php?s=&threadid=41927
.. _here: http://forum.doom9.org/showthread.php?s=&threadid=30587
.. _WarpSharp-package for AviSynth v2.5x: #JapanesePlugin
.. _here: http://www.lalternative.org
.. _here: http://forum.doom9.org/showthread.php?s=&threadid=45181
.. _Version: corefilters/version.htm
.. _AvisynthEditor: http://www.avisynth.org/index.php?page=AvisynthEditor
.. _screenshot: http://www.lalternative.org/img/AvisynthEditor.gif
.. _here: http://www.lalternative.org/
.. _Doom9.org forum:
    http://forum.doom9.org/showthread.php?s=&threadid=49487
.. _AVSGenie: http://www.yeomanfamily.demon.co.uk/avsgenie/avsgenie.htm
.. _here: http://forum.doom9.org/showthread.php?s=&threadid=54090
.. _SwiftAVS (by Snollygoster): http://www.swiftavs.net
.. _discussion: http://forum.doom9.org/showthread.php?s=&threadid=48326
.. _Info: corefilters/info.htm
.. _Prime95: http://www.mersenne.org/freesoft.htm
.. _VBLE codec (by MarcFD):
    http://forum.doom9.org/showthread.php?s=&threadid=38389&pagenumber=5
.. _LocoCodec (by TheRealMoh):
    http://forum.doom9.org/showthread.php?s=&threadid=50363
.. _MJPEG codec: http://forum.doom9.org/showthread.php?s=&threadid=48504
.. _ Lukes homepage: http://neuron2.net/LVG/frameserving.html
.. _ReadAVS: http://www.vcdhelp.com/forum/userguides/87270.php
.. _Bens site: http://math.berkeley.edu/~benrg/avisynth-premiere.html
.. _Video Editors Kit sourceforge page:
    http://sourceforge.net/projects/videoeditorskit/
.. _discussion: http://forum.doom9.org/showthread.php?s=&threadid=49964
.. _here: http://nic.dnsalias.com/WM9Enc.html
.. _Huffyuv:
    http://shelob.mordor.net/dgraft/www.math.berkeley.edu/benrg/index.html
.. _DivX5: http://www.avisynth.org/index.php?page=DivX
.. _ReadAVS: http://www.dvdrhelp.com/forum/userguides/87270.php
.. _ResampleAudio: corefilters/resampleaudio.htm
.. _here: http://www.avisynth.org/index.php?page=AddAudio
.. _colorspace conversion errors:
    http://forum.doom9.org/showthread.php?s=&threadid=27932
.. _PluginPace frameserver (by Satish Kumar):
    http://www.debugmode.com/pluginpac/frameserver.php
.. _discussion: http://forum.doom9.org/showthread.php?s=&threadid=51242
.. _Mpeg decoder plugins for AviSynth v1.0x/v2.0x: #MpegDecoders
.. _Mpeg decoder plugins for AviSynth v2.5x: #MpegDecoders2
.. _dvd2avi: http://www.trbarry.com/DVD2AVIT3.zip
.. _HDTV2MPEG2: http://www.avsforum.com/avs-
    vb/attachment.php?s=&postid=1408610
.. _TSDemux: http://www.avsforum.com/avs-
    vb/showthread.php?s=&threadid=222055
.. _Xmuxer: http://www.moonlight.co.il/download/?dl=xmuxer
.. _threadid=10007:
    http://forum.doom9.org/showthread.php?s=&threadid=10007
.. _threadid=23139:
    http://forum.doom9.org/showthread.php?s=&threadid=23139
.. _Q5.2: #q5.2
.. _AviSource: corefilters/avisource.htm
.. _DirectShowSource: corefilters/directshowsource.htm
.. _mp2: http://www.geocities.wilbertdijkhof/mpa2wav.zip
.. _mp2: http://www.geocities.wilbertdijkhof/qmpeg_mp2.zip
.. _AudioDub: corefilters/audiodub.htm
.. _thread: http://forum.doom9.org/showthread.php?s=&threadid=34350
.. _YUV Formats: http://www.fourcc.org/fccyuv.htm
.. _RGB Formats: http://www.fourcc.org/fccrgb.htm
.. _MSDN YUV Formats:
    http://msdn.microsoft.com/library/default.asp?url=/library/en-
    us/dnwmt/html/YUVFormats.asp
.. _Chroma subsampling by Charles Poyton:
    http://www.inforamp.net/~poynton/PDFs/Chroma_subsampling_notation.pdf
.. _here: quick_ref.htm
.. _WarpEnterprises: http://www.avisynth.org/warpenterprises/
.. _Decomb Filter package (by Donald Graft): http://neuron2.net/mine.html
.. _ViewFields/UnViewFields (by Simon Walters):
    http://www.geocities.com/siwalters_uk/fnews.html
.. _GreedyHMA plugin (by Tom Barry): http://www.trbarry.com/GreedyHMA.zip
.. _Motion compensated deinterlace filter "TomsMoComp" (by Tom Barry):
    http://forum.doom9.org/showthread.php?s=&threadid=28778
.. _SmoothDeinterlacer (by Gunnar Thalin, ported to AviSynth by
    Xesdeeni): http://home.bip.net/gunnart/video/AVSPorts/SmoothDeinterlacer/
.. _"IT" (by thejam79): http://members.tripod.co.jp/thejam79/IT_0051.zip
.. _Translation of README:
    http://www.avisynth.org/index.php?page=IT.txt.en
.. _"AntiComb" (by ?): http://www.geocities.co.jp/SiliconValley-
    Sunnyvale/3109/acomb05.zip
.. _Translation of README:
    http://www.avisynth.org/index.php?page=AntiComb
.. _MiscPlugins: #MiscellaneousPlugins
.. _PeachSmoother (by Lindsey Dubb):
    http://students.washington.edu/ldubb/computer/PeachSmoother.zip
.. _documentation:
    http://students.washington.edu/ldubb/computer/Read_Me_Peach_Smoother.htm
.. _discussion: http://forum.doom9.org/showthread.php?s=&threadid=36575
.. _"MAM" (by Marc FD): http://ziquash.chez.tiscali.fr/ Motion Adaptive
    Mixer
.. _site: http://forum.doom9.org/showthread.php?s=&postid=193412
.. _NoMoSmooth (by SansGrip):
    http://www.jungleweb.net/~sansgrip/avisynth/
.. _documentation: http://www.jungleweb.net/~sansgrip/avisynth
    /NoMoSmooth-readme.html
.. _discussion: http://forum.doom9.org/showthread.php?s=&threadid=37471
.. _Dust (by Steady):
    http://forum.doom9.org/showthread.php?s=&threadid=42749
.. _SpatioTemporal Median Filter "STMedianFilter" (by Tom Barry):
    http://www.trbarry.com/STMedianFilter.zip
.. _Convolution3D (by Vlad59): http://hellninjacommando.com/con3d/
.. _Masked Smoother "msmooth" (by Donald Graft):
    http://forum.doom9.org/showthread.php?s=&threadid=31679
.. _Smoother HiQ(uality) plugin (by Klaus Post): http://cultact-
    server.novi.dk/kpo/avisynth/smooth_hiq_as.html
.. _msoften (by Marc FD):
    http://forum.doom9.org/showthread.php?s=&threadid=44308
.. _here: http://forum.doom9.org/showthread.php?s=&threadid=36148
.. _General convolution plugin (by Richard Berg):
    http://forum.doom9.org/showthread.php?s=&threadid=28318
.. _description: http://forum.doom9.org/showthread.php?s=&threadid=25908
.. _Wavelet Noise Reduction (by thejam):
    http://forum.doom9.org/showthread.php?s=&threadid=31754
.. _documentation:
    http://forum.doom9.org/showthread.php?s=&threadid=31754&pagenumber=2
.. _2D Cleaner Noise Reduction filter "_2DClenYUY2":
    http://members.tripod.co.jp/kiraru2002/
.. _TemporalSoften2 plugin (by Dividee):
    http://forum.doom9.org/showthread.php?s=&threadid=22096
.. _TemporalSmoother plugin (by Dividee):
    http://users.win.be/dividee/avisynth.html
.. _TemporalCleaner (by Jim Casaburi; ported to AviSynth by Vlad59):
    http://forum.doom9.org/showthread.php?s=&threadid=37620
.. _Grape Smoother (by Lindsey Dubb):
    http://students.washington.edu/ldubb/computer/GrapeSmoother.zip
.. _documentation:
    http://students.washington.edu/ldubb/computer/Read_Me_Grape_Smoother.htm
.. _discussion: http://forum.doom9.org/showthread.php?s=&threadid=37196
.. _discussion: http://forum.doom9.org/showthread.php?s=&threadid=29529
.. _Unfilter plugin (by Tom Barry): http://www.trbarry.com/UnFilter.zip
.. _discussion: http://forum.doom9.org/showthread.php?s=&threadid=28197
.. _Lanczos resize filter (Implemented by Nic):
    http://nic.dnsalias.com/lanczos3.zip
.. _SimpleResize plugin (by Tom Barry):
    http://www.trbarry.com/SimpleResize.zip
.. _VobSub plugin (by Gabest): http://vobsub.edensrising.com/
.. _"MPEG2DEC2" (by Tom Barry): http://www.trbarry.com/MPEG2DEC2.zip
.. _discussion: http://forum.doom9.org/attachment.php?s=&postid=185758
.. _"MpegDecoder" (by Nic): http://nic.dnsalias.com/MPEGDecoder.zip
.. _MPASource (by Warpenterprises):
    http://www.avisynth.org/warpenterprises
.. _discussion: http://forum.doom9.org/showthread.php?s=&threadid=41435
.. _AntiBlink (by Kurosu):
    http://forum.doom9.org/showthread.php?s=&threadid=33319
.. _Guava Comb (by Lindsey Dubb):
    http://students.washington.edu/ldubb/computer/GuavaComb.zip
.. _documentation:
    http://students.washington.edu/ldubb/computer/Read_Me_Guava_Comb.htm
.. _discussion: http://forum.doom9.org/showthread.php?s=&threadid=37456
.. _Ghostbuster (by SansGrip):
    http://forum.doom9.org/showthread.php?s=&threadid=35339
.. _Exorcist: http://www.republika.pl/vander74/virtualdub/exorcist.zip
.. _BorderControl plugin (by Simon Walters):
    http://www.geocities.com/siwalters_uk/bdrcntrl.html
.. _AutoCrop plugin (by CropsyX): http://www.videofringe.com/autocrop/
.. _discussion: http://forum.doom9.org/showthread.php?s=&threadid=37204
.. _ImageSequence plugin (by Bzzz2):
    http://forum.doom9.org/showthread.php?s=&threadid=26855
.. _Tweak plugin (by Donald Graft):
    http://shelob.mordor.net/dgraft/mine.html
.. _WarpSharp, Xsharpen, UnsharpMask, KenKunNR, KenKunNRT, UVTimingH,
    UVTimingV, LoadAviUtlInputPlugin, LoadAviUtlFilterPlugin,
    ConvertYUY2ToAviUtlYC, ConvertAviUtlYCToYUY2, EraseGhost, SearchGhost,
    EraseGhostV, SearchGhostV, Auto24FPS, AutoDeint, FrameCache,
    AVIEncodeVideo, LoadPlugin (by ???):
    http://forum.doom9.org/showthread.php?s=&threadid=34076
.. _here: http://www.geocities.co.jp/SiliconValley-PaloAlto/2382/
.. _AviSynth monitor "avsmon" (by johann.Langhofer):
    http://forum.doom9.org/showthread.php?s=&threadid=32125&pagenumber=4
.. _MergeLuma/MergeChroma plugin (by Klaus Post): http://cultact-
    server.novi.dk/kpo/avisynth/merge_as.html
.. _Call (by Nic):
    http://forum.doom9.org/showthread.php?s=&threadid=46506
.. _here: http://forum.doom9.org/showthread.php?s=&threadid=37135
.. _ChromaShift (by Simon Walters):
    http://www.geocities.com/siwalters_uk/chromashift.html
.. _TurnLeft and TurnRight (by Warpenterprises):
    http://forum.doom9.org/showthread.php?s=&threadid=44853
.. _Chr.dll (by WarpEnterprises):
    http://forum.doom9.org/showthread.php?s=&threadid=47972&pagenumber=2
.. _Spray (by WarpEnterprises):
    http://forum.doom9.org/showthread.php?s=&threadid=49557
.. _Zoom "Pan/Zoom/Rotate" (by WarpEnterprises):
    http://forum.doom9.org/showthread.php?s=&postid=283982
.. _MJPEGcorrect plugin:
    http://inmatrix.hoyty.com/mirror/mjpegcorrect.zip
.. _description: http://www.inmatrix.com/articles/ivtcsynth1.shtml
.. _WarpEnterprises: http://www.avisynth.org/users/warpenterprises/
.. _rePal (by Bach):
    http://forum.doom9.org/showthread.php?s=&threadid=48401
.. _Unblend (by Bach):
    http://forum.doom9.org/showthread.php?s=&threadid=55019
.. _discussion: http://neuron2.net/ipw-web/bulletin/bb/viewtopic.php?t=56
.. _Area based deinterlacer (by Donald Graft):
    http://forum.doom9.org/showthread.php?s=&threadid=46161
.. _discussion: http://forum.doom9.org/showthread.php?s=&threadid=55598
.. _discussion: http://neuron2.net/ipw-web/bulletin/bb/viewtopic.php?t=57
.. _discussion: http://forum.doom9.org/showthread.php?s=&threadid=51901&p
    erpage=20&pagenumber=2
.. _Smoothdeinterlacer (recompiled by Donald Graft):
    http://forum.doom9.org/showthread.php?s=&threadid=46161&pagenumber=2
.. _Interpolation Bob (by kevina20723):
    http://forum.doom9.org/showthread.php?s=&threadid=62142
.. _SmartDecimate (by kevina20723):
    http://forum.doom9.org/showthread.php?s=&threadid=60031
.. _discussion: http://neuron2.net/ipw-
    web/bulletin/bb/viewtopic.php?t=61&start=50
.. _TPRIVTC (by Kurosu):
    http://forum.doom9.org/showthread.php?s=&threadid=44854
.. _Progressive Frame Restorer "PFR" (by Simon Walters):
    http://www.geocities.com/siwalters_uk/pfravs.html
.. _discussion: http://forum.doom9.org/showthread.php?s=&threadid=49815
.. _"IT" (by thejam79, recompiled by Donald Graft):
    http://forum.doom9.org/showthread.php?s=&threadid=44872
.. _GreedyHMA (by Tom Barry):
    http://mywebpages.comcast.net/trbarry/downloads.htm
.. _discussion: http://forum.doom9.org/showthread.php?s=&threadid=45995
.. _discussion: http://forum.doom9.org/showthread.php?s=&threadid=37915
.. _discussion: http://forum.doom9.org/showthread.php?s=&threadid=52333
.. _MiscPlugins: #MiscellaneousPlugins2
.. _PeachSmoother (by Lindsey Dubb):
    http://forum.doom9.org/showthread.php?s=&threadid=58674
.. _discussion: http://forum.doom9.org/showthread.php?s=&threadid=38296
.. _MipSmooth filter (by Sh0dan):
    http://forum.doom9.org/showthread.php?s=&threadid=63153
.. _Convolution3DYV12 (by Vlad59):
    http://forum.doom9.org/showthread.php?s=&threadid=49806
.. _discussion: http://forum.doom9.org/showthread.php?s=&threadid=38281
.. _discussion: http://forum.doom9.org/showthread.php?s=&threadid=43976
.. _SmoothUV (by Kurosu):
    http://kurosu.inforezo.org/avs/Smooth/index.html
.. _discussion: http://forum.doom9.org/showthread.php?s=&threadid=60631
.. _VagueDenoiser (by Lefungus):
    http://forum.doom9.org/showthread.php?s=&threadid=56871
.. _Deen (by Marc FD): http://ziquash.chez.tiscali.fr/
.. _discussion: http://forum.doom9.org/showthread.php?s=&threadid=41643
.. _SmoothHiQ (recompiled by Richard):
    http://forum.doom9.org/showthread.php?s=&threadid=45277
.. _TemporalCleaner (by Jim Casaburi; ported to AviSynth by Vlad59): http
    ://forum.doom9.org/showthread.php?s=&threadid=37620&perpage=20&pagenumber
    =3
.. _Chroma Noise Reducer "Cnr2" (by Marc FD):
    http://forum.doom9.org/showthread.php?s=&threadid=44500
.. _discussion:
    http://forum.doom9.org/showthread.php?s=&threadid=29529&pagenumber=2
.. _discussion: http://forum.doom9.org/showthread.php?s=&threadid=42839
.. _discussion: http://forum.doom9.org/showthread.php?s=&threadid=38436
.. _discussion:
    http://forum.doom9.org/showthread.php?s=&threadid=28197&pagenumber=3
.. _discussion: http://forum.doom9.org/showthread.php?s=&threadid=43207
.. _ReduceBy2 replacement for TMPGEnc (by scmccarthy):
    http://forum.doom9.org/showthread.php?s=&postid=378363
.. _discussion: http://forum.doom9.org/showthread.php?s=&postid=271863
.. _VSFilter (by Gabest): http://www.sf.net/projects/guliverkli
.. _discussion: http://forum.doom9.org/showthread.php?s=&threadid=41196
.. _MPEG2DEC (by dividee):
    http://forum.doom9.org/showthread.php?s=&threadid=42301
.. _MPEG2DEC3 (by Marc FD and others):
    http://forum.doom9.org/showthread.php?s=&threadid=53164
.. _Mpegdecoder (by Nic): http://nic.dnsalias.com/MPEGDecoder.html
.. _discussion:
    http://forum.doom9.org/showthread.php?s=&postid=240354#post240354
.. _evilMPASource (by Nic): http://forum.doom9.org/showthread.php?s=&thre
    adid=53164&perpage=20&pagenumber=12
.. _MPASource (by Warpenterprises):
    http://members.aon.at/archi/warpenterprises
.. _SSIM (by Lefungus):
    http://forum.doom9.org/showthread.php?s=&threadid=61128
.. _Super8Equal (by Belgabor):
    http://forum.doom9.org/showthread.php?s=&threadid=48951
.. _discussion:
    http://forum.doom9.org/showthread.php?s=&threadid=37204&pagenumber=2
.. _Declick (by Donald Graft):
    http://forum.doom9.org/showthread.php?s=&threadid=52310
.. _Deflicker filter (by Donald Graft, port of the VirtualDub filter):
    http://forum.doom9.org/showthread.php?s=&threadid=40293
.. _Conditional Temporal Median Filter (by kevina20723):
    http://forum.doom9.org/showthread.php?s=&threadid=57914
.. _X-Logo (by Leuf):
    http://forum.doom9.org/showthread.php?s=&threadid=56660
.. _FixVHSOversharp (by MrTibs):
    http://www.geocities.com/mrtibsvideo/fixvhsoversharp.html
.. _discussion: http://www.kvcd.net/forum/viewtopic.php?t=3119
.. _BorderControl (by Simon Walters):
    http://forum.doom9.org/showthread.php?s=&threadid=45670
.. _discussion: http://forum.doom9.org/showthread.php?s=&threadid=50132
.. _Reinterpolate411 (by Tom Barry):
    http://www.trbarry.com/ReInterpolate411.zip
.. _discussion:
    http://forum.doom9.org/showthread.php?s=&threadid=58294&pagenumber=2
.. _Imagesequence plugin (by Bzzz, modified by Warpenterprises and
    Sh0dan):
    http://forum.doom9.org/showthread.php?s=&threadid=26855&pagenumber=2
.. _ImageReader: corefilters/imagesource.htm
.. _discussion: http://forum.doom9.org/showthread.php?s=&threadid=41850
.. _Convert3d (by hanfrunz):
    http://forum.doom9.org/showthread.php?s=&threadid=48842
.. _AVISynth C API (by kevina20723):
    http://kevin.atkinson.dhs.org/avisynth_c/
.. _discussion: http://forum.doom9.org/showthread.php?s=&threadid=58840
.. _MaskTools (by Kurosu):
    http://forum.doom9.org/showthread.php?s=&threadid=49892
.. _AudioGraph (by Richard Ling, modified by Sh0dan):
    http://forum.doom9.org/showthread.php?s=&threadid=59412
.. _Blockbuster (by Sansgrip, recompiled by CruNcher):
    http://forum.doom9.org/showthread.php?s=&threadid=44927
.. _discussion: http://forum.doom9.org/showthread.php?s=&threadid=46765&p
    erpage=20&pagenumber=2
.. _CompareYV12 (by Shalcker):
    http://web.etel.ru/~shalcker/CompareYV12.zip
.. _discussion: http://forum.doom9.org/showthread.php?s=&threadid=58187
.. _SelectByString (by stickboy):
    http://forum.doom9.org/showthread.php?s=&threadid=60532
.. _discussion: http://forum.doom9.org/showthread.php?s=&threadid=50588
.. _discussion: http://forum.doom9.org/showthread.php?s=&postid=252451
.. _discussion: http://forum.doom9.org/showthread.php?s=&threadid=56036
.. _discussion:
    http://forum.doom9.org/showthread.php?s=&postid=205442#post205442
.. _DVinfo (by WarpEnterprises):
    http://forum.doom9.org/showthread.php?s=&threadid=61688
.. _msvcp71.dll/msvcr71.dll:
    http://www.geocities.com/wilbertdijkhof/71.cab
.. _AvsCompare (by TheWEF and aquaplaning): http://aquaplaning.20m.com/
.. _discussion: http://forum.doom9.org/showthread.php?s=&threadid=40675
.. _AvsTimer (by kassandro):
    http://forum.doom9.org/showthread.php?s=&threadid=56090
.. _AVISynth BatchScripting: http://sourceforge.net/projects/avsbatches
.. _thread: http://forum.doom9.org/showthread.php?s=&threadid=23296
.. _ShareFunctions: http://www.avisynth.org/index.php?page=ShareFunctions
.. _threadid=23804:
    http://forum.doom9.org/showthread.php?s=&threadid=23804
.. _http://neuron2.net/hosted.html: http://neuron2.net/hosted.html
.. _Donald's homepage: http://shelob.mordor.net/dgraft/
.. _SeparateFields: corefilters/separatefields.htm
