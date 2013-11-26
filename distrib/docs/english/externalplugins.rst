
Avisynth 2.5 Selected External Plugin Reference
===============================================


General info
------------

AviSynth plugins are external linked modules (libraries) implementing one or
more additional functions (filters) for deinterlacing, noise reduction, etc.
Great number of plugins (200 or more) were written by independent developers
as free software. You can get them at `collection by WarpEnterprises`_ or
(most recent) at homepages of authors (see also AviSynth Web site and
forums). This documentation includes authors descriptions of selected popular
plugins with typical useful functions. It can be good reading even if you
will use some other (similar) plugins.

The description of a plugin starts with some general info about the plugin.
For example

**author:** Rainer Wittmann (aka kassandro)
**version:** 0.6.1
**download:** `http://www.removedirt.de.tf/`_
**category:** Temporal Smoothers
**requirements:**

-   YV12 & YUY2 Colorspace
-   SSEMMX support
-   width and the height of the clip must be a multiple of 8

**license:** GPL

The first line "**author**" gives the author(s) of the plugin. It can be
his/her real name, the forum nickname, or both.
The second line "**version**" gives the version of the plugin on which is
described in *this* documentation. Note that it might not be the most recent
version of the plugin.
The third line "**download**" gives the download page of the plugin.
The fourth line "**category**", is the category under which the plugin can be
found.
The fifth line "**requirements**", are the requirements for being able to use
the plugin. Requirements can be the supported color space (YV12 and YUY2 in
this case), the supported CPU (which is SSEMMX here) or that the width/height
must be a multiple of some number (usually 8 or 16). The latter is a
requirement for the optimizations in the plugin.
The last line "**license**" gives the license of the plugin. Usually it is
none (ie closed source), GPL or just open source (without a specific
license).

A final note about the CPUs which might be required for a plugin. If you
don't know what kind of optimizing instructions are used by your CPU, you can
look it up in the following table
**optimizing instructions** **CPU**
MMX Pentium MMX, Pentium II, K6, K6II, K6III and later
iSSE (also called SSEMMX) Pentium III, all Duron (called 3DNow extension),
all Athlon (called 3DNow extension)
SSE Pentium III, Duron (core Morgan), Athlon XP and later
SSE2 P-IV, Opteron, Athlon 64
SSE3 P-IV Prescott

Deinterlacing & Pulldown Removal
-----------------

*All PAL, NTSC, and SECAM video is interlaced, which means that only every
other line is broadcast at each refresh interval.  Deinterlacing filters let
you take care of any problems caused by this. IVTC (inverse telecine, aka
pulldown removal) filters undo the telecine process, which comes from
differences between the timing of your video and its original source.*

`Decomb Filter package (by Donald Graft)`_ This package of plugin functions
for AviSynth provides the means for removing combing artifacts from telecined
progressive streams, interlaced streams, and mixtures thereof. Functions can
be combined to implement inverse telecine for both NTSC and PAL streams.
[`discussion`_].
`DGBob (by Donald Graft)`_ This filter splits each field of the source into
its own frame and then adaptively creates the missing lines either by
interpolating the current field or by using the previous field's data.
[`discussion`_].
`FDecimate (by Donald Graft)`_ This filter provides extended decimation
capabilities not available from Decimate(). It can remove frames from a clip
to achieve the desired frame rate, while retaining audio/video
synchronization. It preferentially removes duplicate frames where possible.
[`discussion`_].
`GreedyHMA (by Tom Barry)`_ DScaler's Greedy/HM algorithm code to perform
pulldown matching, filtering, and video deinterlacing. [`discussion`_].
`IBob (by Kevin Atkinson)`_ This simple filter works identically to the
Avisynth built-in Bob filter except that it uses linear interpolation instead
of bicubic resizing. [`discussion`_].
`KernelDeint (by Donald Graft)`_ This filter deinterlaces using a kernel
approach. It gives greatly improved vertical resolution in deinterlaced areas
compared to simple field discarding. [`discussion`_].
`LeakKernelDeint (mod of KernelDeint by Leak)`_ This filter deinterlaces
using a kernel approach. It gives greatly improved vertical resolution in
deinterlaced areas compared to simple field discarding. [`discussion`_].
`MultiDecimate (by Donald Graft)`_ Removes N out of every M frames, taking
the frames most similar to their predecessors. [`discussion`_].
`SmartDecimate (by Kevin Atkinson)`_ This filter removes telecine by
combining telecine fields and decimating at the same time, which is different
from the traditional approach of matching telecine frames and then removing
duplicates. [`discussion`_].
`TDeint (by tritical)`_ TDeint is a bi-directionally, motion adaptive (sharp)
deinterlacer. It can also adaptively choose between using per-field and per-
pixel motion adaptivity. It can use cubic interpolation, kernel interpolation
(with temporal direction switching), or one of two forms of modified ELA
interpolation which help to reduce "jaggy" edges in moving areas where
interpolation must be used. TDeint also supports user overrides through an
input file, and can act as a smart bobber or same frame rate deinterlacer, as
well as an IVTC post-processor. [`discussion`_].
`TIVTC Filter package (by tritical)`_ This package of plugin functions for
AviSynth provides the means for removing combing artifacts from telecined
progressive streams, interlaced streams, and mixtures thereof. Functions can
be combined to implement inverse telecine for both NTSC and PAL streams.
`TomsMoComp "Motion compensated deinterlace filter" (by Tom Barry)`_ This
filter uses motion compensation and adaptive processing to deinterlace video
source (not for NTSC film). [`discussion`_].
`UnComb IVTC (by Tom Barry)`_ Filter for matching up even and odd fields of
properly telecined NTSC or PAL film source video. [`discussion`_].

Spatio-Temporal Smoothers
-------------------------

*These filters use color similarities and differences both within and between
frames to reduce noise and improve compressed size.  They can greatly improve
noisy video, but some care should be taken with them to avoid blurred
movement and loss of detail.*

`Deen (by Marc FD)`_ Several denoisers. [`discussion`_]
`Convolution3D / Convolution3DYV12 (by Vlad59)`_ Convolution3D is a spatio-
temporal smoother, it applies a 3D convolution filter to all pixels of
consecutive frames. [`discussion`_].
`FluxSmooth (by SansGrip)`_ Fluctuating pixels are wiped from existence by
averaging it with its neighbours. [`discussion`_].
`FFT3DFilter (by Fizick)`_ FFT3DFilter is 3D Frequency Domain filter - strong
denoiser and moderate sharpener. [`discussion`_].
`FFT3DGPU (by tsp)`_ FFT3dGPU is a GPU version of FFT3DFilter.
[`discussion`_].
`NoMoSmooth (by SansGrip)`_ A motion-adaptive spatio-temporal smoother.
[`discussion`_].
`MipSmooth (by Sh0dan)`_ It takes the source frame, and creates three new
versions, each half the size of the previous. They are scaled back to
original size. They are compared to the original, and if the difference is
below the threshold, the information is used to form the final pixel.
[`discussion`_].
`PeachSmoother (by Lindsey Dubb)`_ An adaptive smoother optimized for TV
broadcasts. The Peach works by looking for good pixels and gathering orange
smoke from them. When it has gathered enough orange smoke, it sprinkles that
onto the bad pixels, making them better. [`discussion`_].
`STMedianFilter "SpatioTemporal Median Filter" (by Tom Barry)`_
STMedianFilter is a (slightly motion compensated) spatial/temporal median
filter.

Spatial Smoothers
-----------------

*These use color similarities and differences within a frame to improve the
picture and reduce compressed size. They can smooth out noise very well, but
overly aggressive settings for them can cause a loss of detail.*

`MSmooth "Masked Smoother" (by Donald Graft)`_ This filter is effective at
removing mosquito noise as well as effectively smoothing flat areas in anime.
[`discussion`_].
`SmoothUV (by Kurosu)`_ This filter can be used to reduce rainbows, as done
by SmartSmoothIQ. [`discussion`_].
`TBilateral (by tritical)`_ TBilateral is a spatial smoothing filter that
uses the bilateral filtering algorithm. It does a nice job of smoothing while
retaining picture structure. [`discussion`_]
`VagueDenoiser (by Lefungus)`_ A simple denoiser that uses wavelets.
[`discussion`_].

Temporal Smoothers
------------------

*These filters use color similarities and differences between frames to
improve the picture and reduce compressed size.  They can get rid of most
noise in stationary areas without losing detail, but overly strong settings
can cause moving areas to be blurred.*

`Cnr2 "Chroma Noise Reducer" (by Marc FD)`_ Reduces the noise on the chroma
(UV) and preserves the luma (Y). [`discussion`_].
`GrapeSmoother (by Lindsey Dubb)`_ When colors change just a little, the
filter decides that it is probably noise, and only slightly changes the color
from the previous frame. As the change in color increases, the filter becomes
more and more convinced that the change is due to motion rather than noise,
and the new color gets more and more weight. [`discussion`_].
`RemoveDirt (by kassandro)`_ A temporal cleaner with strong protection
against artifacts. [`discussion`_].
`TemporalCleaner (by Jim Casaburi; ported to AviSynth by Vlad59)`_ A simple
but very fast temporal denoiser, aimed to improve compressibility.
`TTempSmooth (by tritical)`_ TTempSmooth is a motion adaptive (it only works
on stationary parts of the picture), temporal smoothing filter.
[`discussion`_]

Sharpen/Soften Plugins
----------------------

*These are closely related to the Spatial Smoothers, above. They attempt to
improve image quality by sharpening or softening edges.*

`asharp (by Marc FD)`_ Adaptive sharpening filter. [`discussion`_].
`aWarpSharp (by Marc FD)`_ A warp sharpening filter.
`MSharpen (by Donald Graft)`_ This plugin for AviSynth implements an unusual
concept in spatial sharpening. Although designed specifically for anime, it
also works quite well on normal video. The filter is very effective at
sharpening important edges without amplifying noise. [`discussion`_].
`TUnsharp (by tritical)`_ TUnsharp is a basic sharpening filter that uses a
couple different variations of unsharpmasking and allows for controlled
sharpening based on edge magnitude and min/max neighborhood value clipping.
The real reason for its existence is that it sports a gui with real time
preview. [`discussion`_].
`Unfilter plugin (by Tom Barry)`_ This filter softens/sharpens a clip.  It
implements horizontal and vertical filters designed to (slightly) reverse
previous efforts at softening or edge enhancment that are common (but ugly)
in DVD mastering. [`discussion`_].
`WarpSharp`_ WarpSharp.
` Xsharpen`_ This filter performs a subtle but useful sharpening effect.

Resizers
--------

*Plugins for resizing your clip.*

`BicublinResize (by Marc FD)`_ This is a set of resamplers: FastBilinear
(similar to tbarry's simpleresize), FastBicubic (an unfiltered Bicubic
resampler) and Bicublin (uses bicubic on Y plane and bilinear on UV planes).
[`discussion`_].
`SimpleResize (by Tom Barry)`_ Very simple and fast two tap linear
interpolation.  It is unfiltered which means it will not soften much.
`YV12InterlacedReduceBy2 (by Tom Barry)`_ InterlacedReduceBy2 is a fast
Reduce By 2 filter, usefull as a very fast downsize of an interlaced clip.
[`discussion`_].

Subtitle (source) Plugins
-------------------------

*Plugins which let you import various subtitle formats (hard-coded).*

`VSFilter (by Gabest)`_ Lets you import various formats of subtitles, like
*.sub, *.srt, *.ssa, *.ass, etc. [`discussion`_].

MPEG Decoder (source) Plugins
-----------------------------

*Plugins which let you import mpeg2 files (including hdtv transport files).*

`DGDecode (by Donald Graft)`_ A MPEG2Dec3 modification. Supports in addition
MPEG-1 files, 4:2:2 input, and a lot of other things. See changelist for more
info. Incompatible with the dvd2avi 1.xx versions and requires DGIndex.
[`discussion`_].
`MPEG2Dec (by dividee and others)`_ Mpeg2dec is a plugin which lets AviSynth
import MPEG2 files. (outputs to YUY2)
`MPEG2Dec3 (by Marc FD and others)`_ A MPEG2Dec2.dll modification with
deblocking and deringing. Note that the colorspace information of dvd2avi is
ignored when using mpeg2dec. [`discussion`_].

Audio Decoder (source) Plugins
------------------------------

*Plugins which let you import audio files.*

`MPASource (by Warpenterprises)`_ A mp1/mp2/mp3 audio decoder plugin.
[`discussion`_].
`NicAudio (by Nic)`_ Audio Plugins for MPEG Audio/AC3/DTS/LPCM. NicLPCMSource
expects raw LPCM files or LPCM WAV files. However, at present it only
supports 2-channel LPCM WAV files. [`discussion`_].

Plugins to compare video quality
--------------------------------

`SSIM (by Lefungus)`_ Filter to compare video quality (similar as psnr, but
using a different video quality metric). [`discussion`_].
`VqmCalc (by Lefungus)`_ Filter to compare video quality (similar as psnr,
but using a different video quality metric). [`discussion`_].

Broadcast Video Plugins
-----------------------

*These are meant to take care of various problems which show up when over the
air video is captured.  Some help with luma/chroma separation; Others reduce
interference problems or compensate for overscan.*

`AutoCrop plugin (by CropsyX)`_ Automatically crops black borders from a
clip. [`discussion`_].
`BorderControl (by Simon Walters)`_ After capturing video you might want to
crop your video to get rid of rubbish.  BorderControl enables you to smear
added borders instead of adding solid borders preventing artefacts between
picture and border. [`discussion`_].
`DeScratch (by Fizick)`_ This plugin removes vertical scratches from films.
[`discussion`_].
`DeSpot (by Fizick)`_ This filter is designed to remove temporal noise in the
form of dots (spots) and streaks found in some videos. The filter is also
useful for restoration (cleaning) of old telecined 8mm (and other) films from
spots (from dust) and some stripes (scratches). [`discussion`_].
`FillMargins (by Tom Barry)`_ A similar filter as BorderControl.
[`discussion`_].
`Guava Comb (by Lindsey Dubb)`_ This is a comb filter, meant to get rid of
rainbows, dot crawl, and shimmering in stationary parts of an image.
[`discussion`_].
`Reinterpolate411 (by Tom Barry)`_ It seems that even chroma pixels are just
being duplicated in the MainConcept codec (NTSC). The new filter will help
that by discarding the odd chroma pixels and recreating them as the average
of the 2 adjacent even pixels. [`discussion`_].
`TComb (by tritical)`_ TComb is a temporal comb filter (it reduces cross-
luminance (rainbowing) and cross-chrominance (dot crawl) artifacts in static
areas of the picture). It will ONLY work with NTSC material, and WILL NOT
work with telecined material where the rainbowing/dotcrawl was introduced
prior to the telecine process! In terms of what it does it is similar to
guavacomb/dedot.

Misc Plugins
------------

`AddGrain (by Tom Barry)`_ AddGrain generates film like grain or other
effects (like rain) by adding random noise to a video clip. This noise may
optionally be horizontally or vertically correlated to cause streaking.
`AudioGraph (by Richard Ling, modified by Sh0dan)`_ Displays the audio
waveform on top of the video. [`discussion`_].
`avsmon "AviSynth monitor" (by johann.Langhofer)`_ This plugin enables you to
preview the video during the conversion and to determine the exact audio
delay. [`discussion`_].
`Blockbuster (by Sansgrip)`_ With this filter one can use several methods to
reduce or eliminate DCT blocks: adding noise (Gaussian distributed),
sharpening, or blurring. [`discussion`_].
`ChromaShift (by Simon Walters)`_ ChromaShift shifts the chrominance
information in any direction, to compensate for incorrect Y/UV registration.
[`discussion`_].
`ColorMatrix (by Wilbert Dijkhof)`_ ColorMatrix corrects the colors of MPEG-2
streams. More correctly, many MPEG-2 streams use slightly different
coefficients (called Rec.709) for storing the color information than
AviSynth's color conversion routines or the XviD/DivX decoders (called
Rec.601) do, with the result that DivX/XviD clips or MPEG-2 clips encoded by
TMPGEnc/QuEnc are displayed with slighty off colors. This can be checked by
opening the MPEG-2 stream directly in VDubMod. [`discussion`_].
`DctFilter (by Tom Barry)`_ Reduces high frequency noise components using
Discrete Cosine Transform and its inverse.  Results in a high compressibility
gain, when it is used at the end of your script.  Height/width must be a
multiple of 16. [`discussion`_].
`DePan (by Fizick)`_ DePan tools estimates global motion (pan) in frames, and
makes full or partial global motion compensation. [`discussion`_].
`Dup (by Donald Graft)`_ This is intended for use in clips that have a
significant number of duplicate content frames, but which differ due to
noise. Typically anime has many such duplicates. By replacing noisy
duplicates with exact duplicates, a bitrate reduction can be achieved.
[`discussion`_].
`DVinfo (by WarpEnterprises)`_ This filter grabs the timestamp and recording
date info out of a DV-AVI. It should work with Type-1 and Type-2, standard
AVI and openDML. [`discussion`_].
`ffavisynth (by Milan Cutka)`_ A plugin which lets you directly use ffdshow
image processing filters from AviSynth scripts. [`discussion`_].
`GiCoCU (by E-Male)`_ Reproduces photoshop's handling amp-files and gimp's
handling of color curve files. [`discussion`_].
`MaskTools (by Kurosu and Manao)`_ This plugin deals with the creation, the
enhancement and the manipulating of such mask for each component of the YV12
colorspace. [`discussion`_].
`MVTools (by Manao)`_ Collection of filters (Blur, ConvertFPS, Denoise,
Interpolate, Mask and others) which uses motion vectors generated by this
plugin. [`discussion`_].
`RawSource (by WarpEnterprises)`_ This filter loads raw video data.
[`discussion`_].
`ReverseFieldDominance (by Simon Walters)`_ Reverses the field dominance of
PAL DV. [`discussion`_].
`TMonitor (by tritical)`_ TMonitor is a filter very similar to AVSMon. It
enables monitoring of an AviSynth clip via previewing the video, viewing clip
information (such as video width, height, colorspace, number of frames, audio
samples, sample rate, number of audio channels, and more), and adjusting the
audio delay. It also supports multiple instances per script, allowing viewing
of differences between different parts of a processing chain.
`Undot (by Tom Barry)`_ UnDot is a simple median filter for removing dots,
that is stray orphan pixels and mosquito noise.  It clips each pixel value to
stay within min and max of its eight surrounding neigbors. [`discussion`_].
`VideoScope (by Randy French)`_ You can use this plugin to graph the colors
of a frame. It shows a waveform monitor (wfm) and a vectorscope.
[`discussion`_].

$Date: 2006/12/18 22:10:10 $

.. _collection by WarpEnterprises: http://avisynth.org/warpenterprises
.. _http://www.removedirt.de.tf/: http://www.removedirt.de.tf/
.. _Decomb Filter package (by   Donald Graft): externalfilters/decomb.htm
.. _discussion: http://forum.doom9.org/showthread.php?s=&threadid=76456
.. _DGBob (by Donald Graft): externalfilters/dgbob.htm
.. _discussion: http://forum.doom9.org/showthread.php?s=&threadid=55598
.. _FDecimate (by Donald   Graft): externalfilters/fdecimate.htm
.. _discussion: http://forum.doom9.org/showthread.php?s=&threadid=77798
.. _GreedyHMA (by Tom Barry): externalfilters/greedyhma.htm
.. _discussion: http://forum.doom9.org/showthread.php?s=&threadid=45995
.. _IBob (by Kevin Atkinson): externalfilters/ibob.htm
.. _discussion: http://forum.doom9.org/showthread.php?s=&threadid=62142
.. _KernelDeint (by Donald   Graft): externalfilters/kerneldeint.htm
.. _discussion: http://neuron2.net/ipw-web/bulletin/bb/viewtopic.php?t=57
.. _LeakKernelDeint   (mod of KernelDeint by Leak):
    externalfilters/leakkerneldeint.htm
.. _discussion: http://forum.doom9.org/showthread.php?t=81322
.. _MultiDecimate (by   Donald Graft): externalfilters/multidecimate.htm
.. _discussion: http://forum.doom9.org/showthread.php?s=&threadid=51901&p
    erpage=20&pagenumber=2
.. _SmartDecimate (by Kevin   Atkinson):
    externalfilters/smartdecimate.htm
.. _discussion: http://forum.doom9.org/showthread.php?s=&threadid=60031
.. _TDeint (by tritical): externalfilters/tdeint.htm
.. _discussion: http://forum.doom9.org/showthread.php?s=&threadid=82264
.. _TIVTC Filter package (by tritical): externalfilters/tivtc.htm
.. _   (by Tom Barry): externalfilters/tomsmocomp.htm
.. _discussion: http://forum.doom9.org/showthread.php?s=&threadid=37915
.. _UnComb IVTC (by Tom Barry): externalfilters/uncomb.htm
.. _discussion: http://forum.doom9.org/showthread.php?s=&threadid=52333
.. _Deen (by Marc FD): externalfilters/deen.htm
.. _discussion: http://forum.doom9.org/showthread.php?s=&threadid=41643
.. _Convolution3D   / Convolution3DYV12 (by Vlad59):
    externalfilters/convolution3d.htm
.. _discussion: http://forum.doom9.org/showthread.php?s=&threadid=38281
.. _FluxSmooth   (by SansGrip): externalfilters/fluxsmooth.htm
.. _discussion: http://forum.doom9.org/showthread.php?s=&threadid=38296
.. _FFT3DFilter (by Fizick): externalfilters/fft3dfilter.htm
.. _discussion: http://forum.doom9.org/showthread.php?t=85790
.. _FFT3DGPU (by tsp): externalfilters/fft3dgpu.htm
.. _discussion: http://forum.doom9.org/showthread.php?t=89941
.. _NoMoSmooth (by SansGrip): externalfilters/nomosmooth.htm
.. _discussion: http://forum.doom9.org/showthread.php?s=&threadid=37471
.. _MipSmooth (by Sh0dan): externalfilters/mipsmooth.htm
.. _discussion: http://forum.doom9.org/showthread.php?s=&threadid=63153
.. _PeachSmoother   (by Lindsey Dubb): externalfilters/peachsmoother.htm
.. _discussion: http://forum.doom9.org/showthread.php?s=&threadid=36575
.. _ (by Tom Barry): externalfilters/stmedianfilter.htm
.. _   (by Donald Graft): externalfilters/msmooth.htm
.. _discussion: http://forum.doom9.org/showthread.php?s=&threadid=43976
.. _SmoothUV   (by Kurosu): externalfilters/smoothuv.htm
.. _discussion: http://forum.doom9.org/showthread.php?s=&threadid=60631
.. _TBilateral (by   tritical): externalfilters/tbilateral.htm
.. _discussion: http://forum.doom9.org/showthread.php?s=&threadid=77856
.. _VagueDenoiser   (by Lefungus): externalfilters/vaguedenoiser.htm
.. _discussion: http://forum.doom9.org/showthread.php?s=&threadid=56871
.. _ (by Marc FD): externalfilters/cnr2.htm
.. _discussion: http://forum.doom9.org/showthread.php?s=&threadid=78905
.. _GrapeSmoother (by Lindsey Dubb): externalfilters/grapesmoother.htm
.. _discussion: http://forum.doom9.org/showthread.php?s=&threadid=37196
.. _RemoveDirt (by   kassandro): externalfilters/removedirt.htm
.. _discussion: http://forum.doom9.org/showthread.php?s=&threadid=70856
.. _TemporalCleaner   (by Jim Casaburi; ported to AviSynth by Vlad59):
    externalfilters/temporalcleaner.htm
.. _TTempSmooth (by   tritical): externalfilters/ttempSmooth.htm
.. _asharp (by Marc FD): externalfilters/asharp.htm
.. _discussion: http://forum.doom9.org/showthread.php?s=&threadid=38436
.. _aWarpSharp (by Marc FD): externalfilters/awarpsharp.htm
.. _MSharpen (by Donald   Graft): externalfilters/msharpen.htm
.. _discussion: http://forum.doom9.org/showthread.php?s=&threadid=42839
.. _TUnsharp (by tritical): externalfilters/tunsharp.htm
.. _discussion: http://forum.doom9.org/showthread.php?t=84344
.. _Unfilter   plugin (by Tom Barry): externalfilters/unfilter.htm
.. _discussion:
    http://forum.doom9.org/showthread.php?s=&threadid=28197&pagenumber=3
.. _WarpSharp: externalfilters/warpsharp.htm
.. _ Xsharpen: externalfilters/xsharpen.htm
.. _BicublinResize (by   Marc FD): externalfilters/bicublinresize.htm
.. _discussion: http://forum.doom9.org/showthread.php?s=&threadid=43207
.. _SimpleResize   (by Tom Barry): externalfilters/simpleresize.htm
.. _YV12InterlacedReduceBy2   (by Tom Barry):
    externalfilters/yv12interlacedreduceby2.htm
.. _discussion: http://forum.doom9.org/showthread.php?s=&postid=271863
.. _VSFilter (by   Gabest): externalfilters/vsfilter.htm
.. _discussion: http://forum.doom9.org/showthread.php?s=&threadid=41196
.. _DGDecode (by Donald   Graft): externalfilters/dgdecode.htm
.. _discussion: http://forum.doom9.org/showthread.php?t=94184
.. _MPEG2Dec   (by dividee and others): externalfilters/mpeg2dec.htm
.. _MPEG2Dec3   (by Marc FD and others): externalfilters/mpeg2dec3.htm
.. _discussion: http://forum.doom9.org/showthread.php?s=&threadid=53164
.. _MPASource   (by Warpenterprises): externalfilters/mpasource.htm
.. _discussion: http://forum.doom9.org/showthread.php?s=&threadid=41435
.. _NicAudio (by Nic): externalfilters/nicaudio.htm
.. _discussion:
    http://forum.doom9.org/showthread.php?s=&threadid=89629pagenumber=2
.. _SSIM   (by Lefungus): externalfilters/ssim.htm
.. _discussion: http://forum.doom9.org/showthread.php?s=&threadid=61128
.. _VqmCalc   (by Lefungus): externalfilters/vqmcalc.htm
.. _discussion: http://forum.doom9.org/showthread.php?s=&threadid=56081
.. _AutoCrop plugin   (by CropsyX): externalfilters/autocrop.htm
.. _discussion: http://forum.doom9.org/showthread.php?t=87602
.. _BorderControl   (by Simon Walters): externalfilters/bordercontrol.htm
.. _discussion: http://forum.doom9.org/showthread.php?s=&threadid=45670
.. _DeScratch (by Fizick): externalfilters/descratch.htm
.. _discussion: http://forum.doom9.org/showthread.php?s=&threadid=67794
.. _DeSpot (by Fizick): externalfilters/despot.htm
.. _discussion: http://forum.doom9.org/showthread.php?s=&threadid=59388
.. _FillMargins   (by Tom Barry): externalfilters/fillmargins.htm
.. _discussion: http://forum.doom9.org/showthread.php?s=&threadid=50132
.. _Guava   Comb (by Lindsey Dubb): externalfilters/guavacomb.htm
.. _discussion: http://forum.doom9.org/showthread.php?s=&threadid=37456
.. _Reinterpolate411   (by Tom Barry):
    externalfilters/reinterpolate411.htm
.. _discussion:
    http://forum.doom9.org/showthread.php?s=&threadid=58294&pagenumber=2
.. _TComb (by tritical): externalfilters/tcomb.htm
.. _AddGrain   (by Tom Barry): externalfilters/addgrain.htm
.. _AudioGraph   (by Richard Ling, modified by Sh0dan):
    externalfilters/audiograph.htm
.. _discussion: http://forum.doom9.org/showthread.php?s=&threadid=59412
.. _ (by johann.Langhofer): externalfilters/avsmon.htm
.. _discussion: http://forum.doom9.org/showthread.php?s=&threadid=32125
.. _Blockbuster   (by Sansgrip): externalfilters/blockbuster.htm
.. _discussion: http://forum.doom9.org/showthread.php?s=&threadid=44927
.. _ChromaShift   (by Simon Walters): externalfilters/chromashift.htm
.. _discussion: http://forum.doom9.org/showthread.php?s=&threadid=33302
.. _ColorMatrix (by   Wilbert Dijkhof): externalfilters/colormatrix.htm
.. _discussion: http://forum.doom9.org/showthread.php?s=&threadid=82217
.. _DctFilter   (by Tom Barry): externalfilters/dctfilter.htm
.. _discussion: http://forum.doom9.org/showthread.php?s=&postid=252451
.. _DePan (by Fizick): externalfilters/depan.htm
.. _discussion: http://forum.doom9.org/showthread.php?s=&threadid=66686
.. _Dup (by Donald Graft): externalfilters/dup.htm
.. _discussion: http://forum.doom9.org/showthread.php?s=&threadid=41850
.. _DVinfo   (by WarpEnterprises): externalfilters/dvinfo.htm
.. _discussion: http://forum.doom9.org/showthread.php?s=&threadid=61688
.. _ffavisynth (by Milan   Cutka): externalfilters/ffavisynth.htm
.. _discussion: http://forum.doom9.org/showthread.php?s=&threadid=85447
.. _GiCoCU (by E-Male): externalfilters/gicocu.htm
.. _discussion: http://forum.doom9.org/showthread.php?t=87791&page=5
.. _MaskTools   (by Kurosu and Manao): externalfilters/masktools.htm
.. _discussion: http://forum.doom9.org/showthread.php?s=&threadid=67232
.. _MVTools (by Manao): externalfilters/mvtools.htm
.. _discussion: http://forum.doom9.org/showthread.php?s=&threadid=76041
.. _RawSource   (by WarpEnterprises): externalfilters/rawsource.htm
.. _discussion: http://forum.doom9.org/showthread.php?s=&threadid=39798
.. _ReverseFieldDominance   (by Simon Walters):
    externalfilters/reversefielddominance.htm
.. _discussion: http://forum.doom9.org/showthread.php?s=&threadid=46765&p
    erpage=20&pagenumber=2
.. _TMonitor (by tritical): externalfilters/tmonitor.htm
.. _Undot   (by Tom Barry): externalfilters/undot.htm
.. _discussion:
    http://forum.doom9.org/showthread.php?s=&postid=205442#post205442
.. _VideoScope (by Randy French): externalfilters/vscope.htm
.. _discussion: http://forum.doom9.org/showthread.php?s=&threadid=76238
