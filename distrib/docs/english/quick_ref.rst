***Abbreviations:***

Named arguments are written as "arg" and are always optional, non-named
optional arguments are placed into [] brackets.
The types of the non-clip-arguments can be int (integer), float, string or
bool.
*[yuy2]* etc. denotes the color formats the filter can deal with. See
`colorspace conversion filters`_ for more details.
*[16 bit, float]* etc, denotes the sample types which are supported by the
audio filter. "float" is the most accurate one.
*[v2.53]* denotes the version of AviSynth (above 2.01) since the filter is
available, or the last changes in the filter.


--------


Alphabetic view
================

`[A]`_ `[B]`_ `[C]`_ `[D]`_ `[E]`_ `[F]`_ `[G]`_ `[H]`_ `[I]`_ [J] `[K]`_
`[L]`_ `[M]`_ `[N]`_ `[O]`_ `[P]`_ [Q] `[R]`_ `[S]`_ `[T]`_ [U] `[V]`_ `[W]`_
[X] [Y] [Z]

`AddBorders`_ *[yv24] [yv16] [yv12] [yv411] [y8] [yuy2] [rgb32] [rgb24]*

-   ``AddBorders`` (clip, int left, int top, int right, int bottom, int
    "color")

`AudioTrim`_

-   ``AudioTrim ``(clip, float start_time, float end_time) *[v2.60]*
-   ``AudioTrim ``(clip, float start_time, float -duration) *[v2.60]*
-   ``AudioTrim ``(clip, float start_time, float "end") *[v2.60]*
-   ``AudioTrim ``(clip, float start_time, float "length") *[v2.60]*

`Amplify / AmplifydB`_ *[16 bit, float]*

-   ``Amplify ``(clip, float amount1 [, ...])
-   ``AmplifydB ``(clip, float amount1 [, ...])

`Animate / ApplyRange`_ *[yv24] [yv16] [yv12] [yv411] [y8] [yuy2] [rgb32]
[rgb24]*

-   ``Animate ``(clip, int start_frame, int end_frame, string filtername,
    start_args, end_args)
-   ``ApplyRange ``(clip, int start_frame, int end_frame, string
    filtername, args)* [v2.51]*

`AssumeFPS`_ *[yv24] [yv16] [yv12] [yv411] [y8] [yuy2] [rgb32] [rgb24]*

-   ``AssumeFPS ``(clip, int numerator , int denominator, bool
    "sync_audio")
-   `` AssumeFPS ``(clip, float fps, bool "sync_audio")
-   `` AssumeFPS `` (clip1, clip2, bool "sync_audio") *[v2.55]*
-   `` AssumeFPS `` (clip, string preset) *[v2.57]*

`AssumeFrameBased / AssumeFieldBased`_ *[yv24] [yv16] [yv12] [yv411] [y8]
[yuy2] [rgb32] [rgb24]*

-   ``AssumeFrameBased ``(clip)
-   ``AssumeFieldBased ``(clip)

`AssumeBFF / AssumeTFF`_ *[yv24] [yv16] [yv12] [yv411] [y8] [yuy2] [rgb32]
[rgb24]*

-   ``AssumeBFF ``(clip)
-   ``AssumeTFF ``(clip)

`AssumeSampleRate`_ *[all]*

-   ``AssumeSampleRate ``(clip, int samplerate)

`AssumeScaledFPS`_ *[yv24] [yv16] [yv12] [yv411] [y8] [yuy2] [rgb32] [rgb24]*

-   ``AssumeScaledFPS ``(clip, int "multiplier", int "divisor", bool
    "sync_audio") *[v2.56]*

`AudioDub / AudioDubEx`_ *[all] *

-   ``AudioDub ``(video_clip, audio_clip)
-   ``AudioDubEx ``(video_clip, audio_clip) *[v2.56]*

`AVISource / OpenDMLSource / AVIFileSource / WAVSource`_

-   ``AVISource ``(string filename [, ...], bool "audio", string
    "pixel_type" [, string fourCC])
-   ``OpenDMLSource ``(string filename [, ...], bool "audio", string
    "pixel_type" [, string fourCC])
-   ``AVIFileSource ``(string filename [, ...], bool "audio", string
    "pixel_type" [, string fourCC])
-   ``WAVSource ``(string filename [, ...])

`BlankClip / Blackness`_ *[yv24] [yv16] [yv12] [yv411] [y8] [yuy2] [rgb32]
[rgb24]*

-   ``BlankClip ``(clip clip, int "length", int "width", int "height",
    string "pixel_type", float "fps", int "fps_denominator",
    int "audio_rate", bool "stereo", bool "sixteen_bit", int "color", int
    "color_yuv")
-   ``BlankClip ``(clip clip, int "length", int "width", int "height",
    string "pixel_type", float "fps", int "fps_denominator",
    int "audio_rate", int "channels", string "sample_type", int "color",
    int "color_yuv") *[v2.58]*
-   ``Blackness ``()

`Blur / Sharpen`_ *[yv24] [yv16] [yv12] [yv411] [y8] [yuy2] [rgb32] [rgb24]*

-   ``Blur ``(clip, float amount)
-   ``Blur ``(clip, float amountH, float amountV)
-   ``Sharpen ``(clip, float amount)
-   ``Sharpen ``(clip, float amountH, float amountV)

`Bob`_ *[yv24] [yv16] [yv12] [yv411] [y8] [yuy2] [rgb32] [rgb24]*

-   ``Bob ``(clip, float "b", float "c", float "height")

`ChangeFPS`_ *[yv24] [yv16] [yv12] [yv411] [y8] [yuy2] [rgb32] [rgb24]*

-   ``ChangeFPS ``(clip, int numerator , int denominator, bool "linear")
    *[v2.50]*
-   ``ChangeFPS ``(clip, float fps, bool "linear") *[v2.50]*
-   ``ChangeFPS ``(clip1, clip2, bool "linear") *[v2.56]*
-   ``ChangeFPS `` (clip, string preset) *[v2.57]*

`ColorBars / ColorBarsHD`_ *[rgb32] [yuy2] [yv12] [yv24]*

-   ``ColorBars ``(int "width", int "height", string "pixel_type")
-   ``ColorBarsHD ``(int "width", int "height", string "pixel_type")
    *[v2.60]*

`ColorYUV`_ *[yv24] [yv16] [yv12] [yv411] [y8] [yuy2] [rgb32] [rgb24]*

-   ColorYUV (clip, float "gain_y", float "off_y", float "gamma_y", float
    "cont_y", float "gain_u", float "off_u", float "gamma_u",
    float "cont_u", float "gain_v", float "off_v", float "gamma_v", float
    "cont_v",
   string "levels", string "opt", bool "showyuv", bool "analyze", bool
   "autowhite", bool "autogain") *[v2.50]*

`ComplementParity`_ *[yv24] [yv16] [yv12] [yv411] [y8] [yuy2] [rgb32]
[rgb24]*

-   ``ComplementParity ``(clip)

`Compare`_ *[yv12] [yuy2] [rgb32] [rgb24] *

-   ``Compare ``(clip_filtered, clip_original, string "channels", string
    "logfile", bool "show_graph")

`ConditionalFilter / ConditionalSelect / FrameEvaluate / ScriptClip`_ /
`ConditionalReader`_ *[yv12] [yuy2] *

-   ``ConditionalFilter ``(clip testclip, clip source1, clip source2,
    string expression1, string operator, string expression2, bool "show")
    *[v2.52]*
-   ``ConditionalSelect ``(clip testclip, string expression, clip
    source0, clip source1, clip source2, ..., bool "show") *[v2.60]*
-   ``FrameEvaluate ``(clip clip, script function, bool "after_frame")
    *[v2.52]*
-   ``ScriptClip ``(clip clip, string function, bool "show", bool
    "after_frame") *[v2.52]*
-   ``ConditionalReader ``(clip clip, string filename, string
    variablename, bool "show") *[v2.54]*

`ConvertAudioTo8bit / ConvertAudioTo16bit / ConvertAudioTo24bit /
ConvertAudioTo32bit / ConvertAudioToFloat`_ *[all] *

-   ``ConvertAudioTo8bit ``(clip) *[v2.50]*
-   ``ConvertAudioTo16bit ``(clip)
-   ``ConvertAudioTo24bit ``(clip) *[v2.53]*
-   ``ConvertAudioTo32bit ``(clip) *[v2.50]*
-   ``ConvertAudioToFloat ``(clip) *[v2.50]*

`ConvertBackToYUY2 / ConvertToRGB / ConvertToRGB24 / ConvertToRGB32 /
ConvertToY8 / ConvertToYUY2 /
ConvertToYV12 / ConvertToYV16 / ConvertToYV24 / ConvertToYV411`_ *[yv24]
[yv16] [yv12] [yv411] [y8] [yuy2] [rgb32] [rgb24]*

-   ``ConvertToRGB ``(clip, string "matrix", bool "interlaced", string
    "ChromaInPlacement", string "chromaresample")
-   ``ConvertToRGB24 ``(clip, string "matrix", bool "interlaced", string
    "ChromaInPlacement", string "chromaresample")
-   ``ConvertToRGB32 ``(clip, string "matrix", bool "interlaced", string
    "ChromaInPlacement", string "chromaresample")
-   ``ConvertToYUY2 ``(clip, bool "interlaced", string "matrix", string
    "ChromaInPlacement", string "chromaresample")
-   ``ConvertToBackYUY2 ``(clip, string "matrix")
-   ``ConvertToY8 ``(clip, string "matrix") *[v 2.60]*
-   ``ConvertToYV12 ``(clip, bool "interlaced", string "matrix", string
    "ChromaInPlacement", string "chromaresample", string
    "ChromaOutPlacement") *[v 2.50]*
-   ``ConvertToYV16 ``(clip, bool "interlaced", string "matrix", string
    "ChromaInPlacement", string "chromaresample") *[v 2.60]*
-   ``ConvertToYV24 ``(clip, bool "interlaced", string "matrix", string
    "ChromaInPlacement", string "chromaresample") *[v 2.60]*
-   ``ConvertToYV411 ``(clip, bool "interlaced", string "matrix", string
    "ChromaInPlacement", string "chromaresample") *[v 2.60]*

`ConvertFPS`_ *[yv24] [yv16] [yv12] [yv411] [y8] [yuy2] [rgb32] [rgb24]*

-   ``ConvertFPS ``(clip, float new_fps, int "zone", int "vbi")
-   ``ConvertFPS ``(clip, int numerator, int denominator, int "zone", int
    "vbi")
-   ``ConvertFPS ``(clip1, clip2, int "zone", int "vbi") *[v2.56]*
-   ``ConvertFPS `` (clip, string preset) *[v2.57]*

`ConvertToMono`_ *[16 bit, float] *

-   ``ConvertToMono ``(clip)

`Crop / CropBottom`_ *[yv24] [yv16] [yv12] [yv411] [y8] [yuy2] [rgb32]
[rgb24]*

-   ``Crop ``(clip, int left, int top, int width, int height, bool
    "align")
-   ``Crop ``(clip, int left, int top, int -right, int -bottom, bool
    "align")
-   ``CropBottom ``(clip, int count,  bool "align")

`DelayAudio`_ *[all] *

-   ``DelayAudio ``(clip, float seconds)

`DeleteFrame`_ *[yv24] [yv16] [yv12] [yv411] [y8] [yuy2] [rgb32] [rgb24]*

-   ``DeleteFrame ``(clip, int frame [, ...])

`DirectShowSource`_

-   ``DirectShowSource ``(string filename, float "fps", bool "seek", bool
    "audio", bool "video", bool "convertfps", bool "seekzero", int "timeout",
    string "pixel_type", int "framecount", string "logfile", int "logmask")

`Dissolve`_ *[yv24] [yv16] [yv12] [yv411] [y8] [yuy2] [rgb32] [rgb24]*

-   ``Dissolve ``(clip1, clip2 [, ...], int overlap, float "fps")

`DoubleWeave`_ *[yv24] [yv16] [yv12] [yv411] [y8] [yuy2] [rgb32] [rgb24]*

-   ``DoubleWeave ``(clip)

`DuplicateFrame`_ *[yv24] [yv16] [yv12] [yv411] [y8] [yuy2] [rgb32] [rgb24]*

-   ``DuplicateFrame ``(clip, int frame [, ...])

`Echo`_ *[all] *

-   ``Echo ``(clip1, clip2 [, ...])

`EnsureVBRMP3Sync`_ *[all] *

-   ``EnsureVBRMP3Sync ``(clip)

`FadeIn0 / FadeIO0 / FadeOut0
FadeIn / FadeIO / FadeOut
FadeIn2 / FadeIO2/ FadeOut2`_ *[yv24] [yv16] [yv12] [yv411] [y8] [yuy2]
[rgb32] [rgb24]*

-   ``FadeIn0 ``(clip, int frames, int "color", float "fps") *[v2.56]*
-   ``FadeIn ``(clip, int frames, int "color", float "fps")
-   ``FadeIn2 ``(clip, int frames, int "color", float "fps")
-   ``FadeIO0 ``(clip, int frames, int "color", float "fps") *[v2.56]*
-   ``FadeIO ``(clip, int frames, int "color", float "fps")
-   ``FadeIO2 ``(clip, int frames, int "color", float "fps")
-   ``FadeOut0 ``(clip, int frames, int "color", float "fps") *[v2.56]*
-   ``FadeOut ``(clip, int frames, int "color", float "fps")
-   ``FadeOut2 ``(clip, int frames, int "color", float "fps")

`FixBrokenChromaUpsampling`_ *[yuy2] *

-   ``FixBrokenChromaUpsampling ``(clip)

`FixLuminance`_ *[yuy2] *

-   ``FixLuminance ``(clip, int intercept, int slope)

`FlipHorizontal / FlipVertical`_ *[yv24] [yv16] [yv12] [yv411] [y8] [yuy2]
[rgb32] [rgb24]*

-   ``FlipHorizontal ``(clip) *[v2.50]*
-   ``FlipVertical ``(clip)

`FreezeFrame`_ *[yv24] [yv16] [yv12] [yv411] [y8] [yuy2] [rgb32] [rgb24]*

-   ``FreezeFrame ``(clip, int first_frame, int last_frame, int
    source_frame)

`GeneralConvolution`_ *[rgb32] *

-   ``GeneralConvolution ``(clip, int "bias", string "matrix", float
    "divisor", bool "auto") *[v2.55]*

`GetChannel`_ *[all] *

-   ``GetChannel ``(clip, int ch1 [, int ch2, ...]) *[v2.50]*
-   ``GetChannels ``(clip, int ch1 [, int ch2, ...]) *[v2.50]*

`Greyscale`_ *[yv24] [yv16] [yv12] [yv411] [y8] [yuy2] [rgb32] [rgb24]*

-   ``Greyscale ``(clip, string "matrix")

`Histogram`_ *[yv12] [yuy2] *

-   ``Histogram ``(clip, string ''mode'') *[v2.54]*

`ImageReader / ImageSource/ ImageSourceAnim`_ / ` ImageWriter`_ *[yv12] [y8]
[yuy2] [rgb32] [rgb24] *

-   ``ImageReader ``(string "path", int "start", int "end", float "fps",
    bool "use_DevIL", bool "info", string "pixel_type") *[v2.52]*
-   ``ImageSource ``(string "path", int "start", int "end", float "fps",
    bool "use_DevIL", bool "info", string "pixel_type") *[v2.55]*
-   ``ImageSourceAnim ``(string "file", float "fps", bool "info", string
    "pixel_type") *[v2.60]*
-   ``ImageWriter ``(clip, string "path", int "start", int "end", string
    "type", bool "info") *[v2.52]*

`Import`_

-   ``Import ``(string [, ...])

`Info`_ *[yv24] [yv16] [yv12] [yv411] [y8] [yuy2] [rgb32] [rgb24]*

-   ``Info ``(clip) *[v2.50]*

`Interleave`_ *[yv24] [yv16] [yv12] [yv411] [y8] [yuy2] [rgb32] [rgb24]*

-   ``Interleave ``(clip1, clip2 [, ...])

`Invert`_ *[yv12, v2.55] [yuy2, v2.55] [rgb32] [rgb24, v2.55]*

-   ``Invert ``(clip, string "channels") *[v2.53]*

`KillAudio`_ *[all] *

-   ``KillAudio ``(clip)

`KillVideo`_ *[all] *

-   ``KillVideo ``(clip) *[v2.57]*

`Layer / Mask / ResetMask / ColorKeyMask`_ *[RGB32] *

-   ``Layer ``(clip, layer_clip, string "op", int "level", int "x", int
    "y", int "threshold", bool "use_chroma") *[yuy2] [rgb32]*
-   ``Mask ``(clip, mask_clip) *[rgb32]*
-   ``ResetMask ``(clip) *[rgb32]*
-   ``ColorKeyMask ``(clip, int "color", int "tolB" [, int "tolG", int
    "tolR"])* [rgb32]*

`Letterbox`_ *[yv24] [yv16] [yv12] [yv411] [y8] [yuy2] [rgb32] [rgb24]*

-   ``Letterbox ``(clip, int top, int bottom [, int left, int right])

`Levels`_ *[yv24] [yv16] [yv12] [yv411] [y8] [yuy2] [rgb32] [rgb24]*

-   ``Levels ``(clip, int input_low, float gamma, int input_high, int
    output_low, int output_high, bool "coring", bool "dither")

`Limiter`_ *[yv24] [yv16] [yv12] [yv411] [y8] [yuy2]*

-   ``Limiter ``(clip, int "min_luma", int "max_luma", int "min_chroma",
    int "max_chroma" [, string show])* [v2.50]*

`Loop`_ *[yv24] [yv16] [yv12] [yv411] [y8] [yuy2] [rgb32] [rgb24]*

-   ``Loop ``(clip, int "times", int "start", int "end")

`MaskHS`_ *[yv24] [yv16] [yv12] [yv411] [yuy2] [2.60]*

-   ``MaskHS ``(clip, float "startHue", float "endHue", float "maxSat",
    float "minSat", bool "coring")

`MergeARGB / MergeRGB`_ *[yv24] [yv16] [yv12] [yv411] [y8] [yuy2] [rgb32]
[rgb24] [v2.56]*

-   ``MergeARGB ``(clipA, clipR, clipG, clipB)
-   ``MergeRGB ``(clipR, clipG, clipB [, string "pixel_type"])

`MergeChannels`_ *[all] *

-   ``MergeChannels ``(clip1, clip2 [, ...])* [v2.50]*

`Merge / MergeChroma / MergeLuma`_ *[yv24] [yv16] [yv12] [yv411] [y8] [yuy2]*

-   ``Merge ``(clip1, clip2, float "weight")   *[yv12, yuy2, rgb32,
    rgb24] [v2.56] *
-   ``MergeChroma ``(clip1, clip2, float "weight")
-   ``MergeLuma ``(clip1, clip2, float "weight")

`MessageClip`_ *[rgb32] *

-   ``MessageClip ``(string message, int "width", int "height", bool
    "shrink", int "text_color", int "halo_color", int "bg_color")

`MixAudio`_ *[16 bit, float] *

-   ``MixAudio ``(clip1, clip 2, float clip1_factor, float
    "clip2_factor")

`Normalize`_ *[16 bit, float] *

-   ``Normalize ``(clip, float "volume", bool "show")

`Overlay`_ *[yv24] [yv16] [yv12] [yv411] [y8] [yuy2] [rgb32] [rgb24]*

-   ``Overlay ``(clip, clip overlay, int "x", int "y", clip "mask", float
    "opacity", string "mode", bool "greymask",
   string "output", bool "ignore_conditional", bool "pc_range") *[v2.54]*

`PeculiarBlend`_ *[yuy2] *

-   ``PeculiarBlend ``(clip, int cutoff)

`Preroll`_ *[all]*

-   ``Preroll ``(clip, int "video", float "audio")

`Pulldown`_ *[yv24] [yv16] [yv12] [yv411] [y8] [yuy2] [rgb32] [rgb24]*

-   ``Pulldown ``(clip, int a , int b)

`RGBAdjust`_ *[rgb32] [rgb24] *

-   ``RGBAdjust ``(clip, float "r", float "g", float "b", float "a",
    float "rb", float "gb", float "bb", float "ab", float "rg", float "gg",
    float "bg", float "ag", bool "analyze", bool "dither")

`ReduceBy2 / HorizontalReduceBy2 / VerticalReduceBy2`_ *[yv24] [yv16] [yv12]
[yv411] [y8] [yuy2] [rgb32] [rgb24]*

-   ``HorizontalReduceBy2 ``(clip)
-   ``VerticalReduceBy2 ``(clip)
-   ``ReduceBy2 ``(clip)

`ResampleAudio`_ *[16 bit, float] *

-   ``ResampleAudio ``(clip, int new_rate_numberator [, int
    new_rate_denominator])

`BilinearResize / BicubicResize / BlackmanResize / GaussResize /
LanczosResize / Lanczos4Resize / PointResize / SincResize / Spline16Resize /
Spline36Resize / Spline64Resize`_ *[yv24] [yv16] [yv12] [yv411] [y8] [yuy2]
[rgb32] [rgb24]*

-   ``BilinearResize ``(clip, int target_width, int target_height, float
    "src_left", float "src_top", float "src_width", float "src_height")
-   ``BicubicResize ``(clip, int target_width, int target_height, float
    "b=1./3.", float "c=1./3.", float "src_left", float "src_top", float
    "src_width", float "src_height")
-   ``BlackmanResize ``(clip, int target_width, int target_height, float
    "src_left", float "src_top", float "src_width", float "src_height", int
    "taps=4") *[v2.58]*
-   ``GaussResize ``(clip, int target_width, int target_height, float
    "src_left", float "src_top", float "src_width", float "src_height", float
    "p=30.0") *[v2.56]*
-   ``LanczosResize ``(clip, int target_width, int target_height, float
    "src_left", float "src_top", float "src_width", float "src_height", int
    "taps=3")
-   ``Lanczos4Resize ``(clip, int target_width, int target_height, float
    "src_left", float "src_top", float "src_width", float "src_height")
    *[v2.55]*
-   ``PointResize ``(clip, int target_width, int target_height, float
    "src_left", float "src_top", float "src_width", float "src_height")
-   ``SincResize ``(clip, int target_width, int target_height, float
    "src_left", float "src_top", float "src_width", float "src_height", int
    "taps=4") *[v2.6]*
-   ``Spline16Resize ``(clip, int target_width, int target_height, float
    "src_left", float "src_top", float "src_width", float "src_height")
    *[v2.56]*
-   ``Spline36Resize ``(clip, int target_width, int target_height, float
    "src_left", float "src_top", float "src_width", float "src_height")
    *[v2.56]*
-   ``Spline64Resize ``(clip, int target_width, int target_height, float
    "src_left", float "src_top", float "src_width", float "src_height")
    *[v2.58]*
-   all resizers: ``xxxResize ``(clip, int target_width, int
    target_height, float "src_left", float "src_top", float -"src_right",
    float -"src_bottom") *[v2.56]*

`Reverse`_ *[yv24] [yv16] [yv12] [yv411] [y8] [yuy2] [rgb32] [rgb24]*

-   ``Reverse ``(clip)

`SegmentedAVISource / SegmentedDirectShowSource`_

-   ``SegmentedAVISource ``(string base_filename [, ...], bool "audio")
-   ``SegmentedDirectShowSource ``(string base_filename [, ...]  [, fps])

`SelectEven / SelectOdd`_ *[yv24] [yv16] [yv12] [yv411] [y8] [yuy2] [rgb32]
[rgb24]*

-   ``SelectEven ``(clip)
-   ``SelectOdd ``(clip)

`SelectEvery`_ *[yv24] [yv16] [yv12] [yv411] [y8] [yuy2] [rgb32] [rgb24]*

-   ``SelectEvery ``(clip, int step_size, int offset1 [, int offset2 [,
    ...]])

`SelectRangeEvery`_ *[yv24] [yv16] [yv12] [yv411] [y8] [yuy2] [rgb32]
[rgb24]*

-   ``SelectRangeEvery ``(clip, int every, int length, int "offset", bool
    "audio'') *[v2.50]*

`SeparateFields`_ *[yv24] [yv16] [yv12] [yv411] [y8] [yuy2] [rgb32] [rgb24]*

-   ``SeparateFields ``(clip)
-   ``SeparateColumns ``(clip, int interval) *[v2.60]*
-   ``SeparateRows ``(clip, int interval) *[v2.60]*

`ShowAlpha`_ *[rgb32] *

-   ``ShowAlpha ``(clip, string "pixel_type") *[v2.54]*

`ShowRed, ShowGreen, ShowBlue`_ *[rgb24] [rgb32] [v2.56]*

-   ``ShowRed ``(clip, string "pixel_type")
-   ``ShowGreen ``(clip, string "pixel_type")
-   ``ShowBlue ``(clip, string "pixel_type")

`ShowFiveVersions`_ * [yv12] [yuy2] [rgb32] [rgb24]*

-   ``ShowFiveVersions ``(clip1, clip2, clip3, clip4, clip5)

`ShowFrameNumber / ShowSMPTE / ShowTime`_ *[yv12] [yuy2] [rgb32] [rgb24] *

-   ``ShowFrameNumber ``(clip, bool "scroll", int "offset", float "x",
    float "y", string "font", int "size", int "text_color", int "halo_color",
    float "font_width", float "font_angle")
-   ``ShowSMPTE ``(clip, float "fps", string "offset", int "offset_f",
    float "x", float "y", string "font", int "size", int "text_color", int
    "halo_color", float "font_width", float "font_angle")
-   ``ShowTime ``(clip, int "offset_f", float "x", float "y", string
    "font", int "size", int "text_color", int "halo_color", float
    "font_width", float "font_angle")* [v2.58]*

`SkewRows`_ * [y8] [yuy2] [rgb32] [rgb24]*

-   ``SkewRows ``(clip, int skew) *[v2.60]*

` SoundOut`_ *[all] [v2.60] *

-   ``SoundOut`` (string output, string filename, bool "showprogress",
    string overwritefile, bool "autoclose", bool "silentblock", bool
    "addvideo", ` special parameters`_)
(the special parameters are output dependent and they are explained in the
documentation itself)

`SpatialSoften / TemporalSoften`_ *[yv12] [yuy2] [rgb32, v2.56] *

-   ``SpatialSoften ``(clip, int radius, int luma_threshold, int
    chroma_threshold)
-   ``TemporalSoften ``(clip, int radius, int luma_threshold, int
    chroma_threshold, int "scenechange", int "mode")* [v2.50]*

`AlignedSplice / UnalignedSplice`_ *[yv24] [yv16] [yv12] [yv411] [y8] [yuy2]
[rgb32] [rgb24]*

-   ``AlignedSplice ``(clip1, clip2 [, ...])
-   ``UnAlignedSplice ``(clip1, clip2 [, ...])

`SSRC`_ *[float] *

-   ``SSRC ``(clip, int samplerate, bool "fast") *[v2.54]*

`StackHorizontal / StackVertical`_ *[yv24] [yv16] [yv12] [yv411] [y8] [yuy2]
[rgb32] [rgb24]*

-   ``StackHorizontal ``(clip1, clip2 [, ...])
-   ``StackVertical ``(clip1, clip2 [, ...])

`Subtitle`_ *[yv24] [yv16] [yv12] [yv411] [y8] [yuy2] [rgb32] [rgb24]*

-   ``Subtitle ``(clip, string text, float "x", float "y", int
    "first_frame", int "last_frame", string "font", int "size", int
    "text_color", int "halo_color", int "lsp", float "font_width", float
    "font_angle", bool "interlaced")
-   ``Subtitle ``(clip, string "text")

`Subtract`_ *[yv24] [yv16] [yv12] [yv411] [y8] [yuy2] [rgb32] [rgb24]*

-   ``Subtract ``(clip1, clip2)

`SuperEQ`_ *[float] *

-   ``SuperEQ ``(clip, string filename) *[v2.54]*
-   ``SuperEQ ``(clip, float band1 [, float band1, ..., float band18])
    *[v2.60]*

`SwapUV / UToY / VToY / YToUV`_ *[yv24] [yv16] [yv12] [yv411] [y8] [yuy2]*

-   ``SwapUV ``(clip) *[v2.50]*
-   ``UToY ``(clip) *[v2.50]*
-   ``UToY8 ``(clip) *[v2.60]*
-   ``VToY ``(clip) *[v2.50]*
-   ``VToY8 ``(clip) *[v2.60]*
-   ``YToUV ``(clip clipU, clip clipV [, clip clipY]) *[v2.50, v2.51]*

`SwapFields`_ *[yv24] [yv16] [yv12] [yv411] [y8] [yuy2] [rgb32] [rgb24]*

-   ``SwapFields ``(clip)

`TCPDeliver`_

-   ``TCPServer`` (clip, int "port") *[v2.55]*
-   ``TCPSource`` (string hostname, int "port", string "compression")
    *[v2.55]*

`TimeStretch`_ *[float] *

-   ``TimeStretch ``(clip, float "tempo", float "rate", float "pitch",
    int "sequence", int "seekwindow", int "overlap", bool "quickseek", int
    "aa") *[v2.57]*

`Tone`_ *[float] *

-   ``Tone ``(float "length", float "frequency", int "samplerate", int
    "channels", string "type", float "level") *[v2.54]*

`Trim`_ *[yv24] [yv16] [yv12] [yv411] [y8] [yuy2] [rgb32] [rgb24]*

-   ``Trim ``(clip, int first_frame, int last_frame [, bool "pad"])
    *[v2.56]*
-   ``Trim ``(clip, int first_frame, int -num_frames [, bool "pad"])
    *[v2.56]*
-   ``Trim ``(clip, int start_time, int "end" [, bool "pad"]) *[v2.60]*
-   ``Trim ``(clip, int start_time, int "length" [, bool "pad"])
    *[v2.60]*

`TurnLeft / TurnRight / Turn180`_ *[yv24] [yv16] [yv12] [yv411] [y8] [yuy2]
[rgb32] [rgb24]*

-   ``TurnLeft ``(clip) *[v2.51]*
-   ``TurnRight ``(clip) *[v2.51]*
-   ``Turn180 ``(clip) *[v2.55]*

`Tweak`_ *[yv24] [yv16] [yv12] [yv411] [y8] [yuy2]*

-   ``Tweak ``(clip, float "hue", float "sat", float "bright", float
    "cont", bool "coring", bool "sse", float "startHue", float "endHue",
    float "maxSat", float "minSat", float "interp", bool "dither")

`Version`_ *[rgb24] *

-   ``Version ``()

`Weave`_ *[yv24] [yv16] [yv12] [yv411] [y8] [yuy2] [rgb32] [rgb24]*

-   ``Weave ``(clip)
-   ``WeaveColumns ``(clip, int period) *[v2.60]*
-   ``WeaveRows ``(clip, int period) *[v2.60]*

`WriteFile / WriteFileIf / WriteFileStart / WriteFileEnd`_ *[yv12] [yuy2]
[rgb32] [rgb24] *

-   ``WriteFile ``(clip, string filename, *string expression1 [, string
    expression2 [, ...]], bool "append", bool "flush"*)
-   ``WriteFileIf ``(clip, string filename, *string expression1 [, string
    expression2 [, ...]], bool "append", bool "flush"*)
-   ``WriteFileStart ``(clip, string filename, *string expression1 [,
    string expression2 [, ...]], bool "append"*)
-   ``WriteFileEnd ``(clip, string filename, *string expression1 [,
    string expression2 [, ...]], bool "append"*)

`[A]`_ `[B]`_ `[C]`_ `[D]`_ `[E]`_ `[F]`_ `[G]`_ `[H]`_ `[I]`_ [J] `[K]`_
`[L]`_ `[M]`_ `[N]`_ `[O]`_ `[P]`_ [Q] `[R]`_ `[S]`_ `[T]`_ [U] `[V]`_ `[W]`_
[X] [Y] [Z]

$Date: 2013/01/06 13:38:34 $

.. _colorspace conversion filters: corefilters/convert.htm
.. _[A]: #A
.. _[B]: #B
.. _[C]: #C
.. _[D]: #D
.. _[E]: #E
.. _[F]: #F
.. _[G]: #G
.. _[H]: #H
.. _[I]: #I
.. _[K]: #K
.. _[L]: #L
.. _[M]: #M
.. _[N]: #N
.. _[O]: #O
.. _[P]: #P
.. _[R]: #R
.. _[S]: #S
.. _[T]: #T
.. _[V]: #V
.. _[W]: #W
.. _AddBorders: corefilters/addborders.htm
.. _AudioTrim: corefilters/trim.htm
.. _Amplify / AmplifydB: corefilters/amplify.htm
.. _Animate / ApplyRange: corefilters/animate.htm
.. _AssumeFPS: corefilters/fps.htm
.. _AssumeFrameBased / AssumeFieldBased:
    corefilters/parity.htm#assumeframefield
.. _AssumeBFF / AssumeTFF: corefilters/parity.htm#assumefieldfirst
.. _AssumeSampleRate: corefilters/assumerate.htm
.. _AssumeScaledFPS: corefilters/fps.htm#AssumeScaledFPS
.. _AudioDub / AudioDubEx: corefilters/audiodub.htm
.. _AVISource / OpenDMLSource / AVIFileSource  / WAVSource:
    corefilters/avisource.htm
.. _BlankClip / Blackness: corefilters/blankclip.htm
.. _Blur / Sharpen: corefilters/blur.htm
.. _Bob: corefilters/bob.htm
.. _ChangeFPS: corefilters/fps.htm#ChangeFPS
.. _ColorBars / ColorBarsHD: corefilters/colorbars.htm
.. _ColorYUV: corefilters/coloryuv.htm
.. _ComplementParity: corefilters/parity.htm#complementparity
.. _Compare: corefilters/compare.htm
.. _ConditionalFilter / ConditionalSelect /    FrameEvaluate /
    ScriptClip: corefilters/conditionalfilter.htm
.. _ConditionalReader: corefilters/conditionalreader.htm
.. _ConvertAudioTo8bit / ConvertAudioTo16bit  / ConvertAudioTo24bit /
    ConvertAudioTo32bit / ConvertAudioToFloat: corefilters/convertaudio.htm
.. _ConvertFPS: corefilters/fps.htm#ConvertFPS
.. _ConvertToMono: corefilters/converttomono.htm
.. _Crop / CropBottom: corefilters/crop.htm
.. _DelayAudio: corefilters/delayaudio.htm
.. _DeleteFrame: corefilters/deleteframe.htm
.. _DirectShowSource: corefilters/directshowsource.htm
.. _Dissolve: corefilters/dissolve.htm
.. _DoubleWeave: corefilters/doubleweave.htm
.. _DuplicateFrame: corefilters/duplicateframe.htm
.. _Echo: corefilters/echo.htm
.. _EnsureVBRMP3Sync: corefilters/ensuresync.htm
.. _ FadeIn2 / FadeIO2/ FadeOut2: corefilters/fade.htm
.. _FixBrokenChromaUpsampling: corefilters/fixbrokenchromaupsampling.htm
.. _FixLuminance: corefilters/fixluminance.htm
.. _FlipHorizontal / FlipVertical: corefilters/flip.htm
.. _FreezeFrame: corefilters/freezeframe.htm
.. _GeneralConvolution: corefilters/convolution.htm
.. _GetChannel: corefilters/getchannel.htm
.. _Greyscale: corefilters/greyscale.htm
.. _Histogram: corefilters/histogram.htm
.. _ImageReader / ImageSource/ ImageSourceAnim:
    corefilters/imagesource.htm
.. _ ImageWriter: corefilters/imagewriter.htm
.. _Import: corefilters/import.htm
.. _Info: corefilters/info.htm
.. _Interleave: corefilters/interleave.htm
.. _Invert: corefilters/invert.htm
.. _KillAudio: corefilters/killaudio.htm
.. _Layer / Mask / ResetMask / ColorKeyMask: corefilters/layer.htm
.. _Letterbox: corefilters/letterbox.htm
.. _Levels: corefilters/levels.htm
.. _Limiter: corefilters/limiter.htm
.. _Loop: corefilters/loop.htm
.. _MaskHS: corefilters/maskhs.htm
.. _MergeARGB / MergeRGB: corefilters/mergergb.htm
.. _MergeChannels: corefilters/mergechannels.htm
.. _Merge / MergeChroma / MergeLuma: corefilters/merge.htm
.. _MessageClip: corefilters/message.htm
.. _MixAudio: corefilters/mixaudio.htm
.. _Normalize: corefilters/normalize.htm
.. _Overlay: corefilters/overlay.htm
.. _PeculiarBlend: corefilters/peculiar.htm
.. _Preroll: corefilters/preroll.htm
.. _Pulldown: corefilters/pulldown.htm
.. _RGBAdjust: corefilters/adjust.htm
.. _ReduceBy2 / HorizontalReduceBy2 / VerticalReduceBy2:
    corefilters/reduceby2.htm
.. _ResampleAudio: corefilters/resampleaudio.htm
.. _BilinearResize / BicubicResize / BlackmanResize  / GaussResize /
    LanczosResize / Lanczos4Resize  / PointResize / SincResize /
    Spline16Resize / Spline36Resize / Spline64Resize: corefilters/resize.htm
.. _Reverse: corefilters/reverse.htm
.. _SegmentedAVISource / SegmentedDirectShowSource:
    corefilters/segmentedsource.htm
.. _SelectEven / SelectOdd: corefilters/select.htm
.. _SelectEvery: corefilters/selectevery.htm
.. _SelectRangeEvery: corefilters/selectrangeevery.htm
.. _SeparateFields: corefilters/separatefields.htm
.. _ShowAlpha: corefilters/showalpha.htm
.. _ShowFiveVersions: corefilters/showfive.htm
.. _ShowFrameNumber / ShowSMPTE / ShowTime: corefilters/showframes.htm
.. _SkewRows: corefilters/skewrows.htm
.. _ SoundOut: corefilters/soundout.htm
.. _SpatialSoften / TemporalSoften: corefilters/soften.htm
.. _AlignedSplice / UnalignedSplice: corefilters/splice.htm
.. _SSRC: corefilters/ssrc.htm
.. _StackHorizontal / StackVertical: corefilters/stack.htm
.. _Subtitle: corefilters/subtitle.htm
.. _Subtract: corefilters/subtract.htm
.. _SuperEQ: corefilters/supereq.htm
.. _SwapUV / UToY / VToY / YToUV: corefilters/swap.htm
.. _SwapFields: corefilters/swapfields.htm
.. _TCPDeliver: corefilters/tcpdeliver.htm
.. _TimeStretch: corefilters/timestretch.htm
.. _Tone: corefilters/tone.htm
.. _TurnLeft / TurnRight / Turn180: corefilters/turn.htm
.. _Tweak: corefilters/tweak.htm
.. _Version: corefilters/version.htm
.. _Weave: corefilters/weave.htm
.. _WriteFile / WriteFileIf / WriteFileStart / WriteFileEnd:
    corefilters/write.htm
