
Filters with multiple input clips
---------------------------------

There are some functions which combine two or more clips in different ways.
How the video content is calculated is described for each function, but here
is a summary which properties the result clip will have.

The input clips must always have the same color format and - with the
exception of `Layer`_ and `Overlay`_ - the same dimensions.

filter framerate framecount audio content audio sampling rate
`AlignedSplice`_, `UnalignedSplice`_ first clip sum of all clips see filter
description first clip
`Dissolve`_ first clip sum of all clips minus the overlap see filter
description first clip
`Merge`_, `MergeLuma`_, `MergeChroma`_, `Merge(A)RGB`_ first clip first clip
(the last frame of the shorter clip is repeated until the end of the clip)
first clip first clip
`Layer`_ first clip first clip (the last frame of the shorter clip is
repeated until the end of the clip) first clip first clip
`Subtract`_ first clip longer clip (the last frame of the shorter clip is
repeated until the end of the clip) first clip first clip
`StackHorizontal`_, `StackVertical`_ first clip longer clip (the last frame
of the shorter clip is repeated until the end of the clip) first clip first
clip
`Interleave`_ (fps of first clip) x (number of clips) N x frame-count of
longer clip (the last frame of the shorter clip is repeated until the end of
the clip) first clip first clip

As you can see the functions are not completely symmetric but take some
attributes from the FIRST clip.

$Date: 2008/07/19 15:17:14 $

.. _Layer: corefilters/layer.htm (Layer)
.. _Overlay: corefilters/Overlay.htm (Overlay)
.. _AlignedSplice: corefilters/splice.htm (AlignedSplice)
.. _UnalignedSplice: corefilters/splice.htm (UnalignedSplice)
.. _Dissolve: corefilters/dissolve.htm (Dissolve)
.. _Merge: corefilters/merge.htm (Merge)
.. _MergeLuma: corefilters/merge.htm (MergeLuma)
.. _MergeChroma: corefilters/merge.htm (MergeChroma)
.. _Merge(A)RGB: corefilters/mergergb.htm (MergeARGB)
.. _Subtract: corefilters/subtract.htm (Subtract)
.. _StackHorizontal: corefilters/stack.htm (StackHorizontal)
.. _StackVertical: corefilters/stack.htm (StackVertical)
.. _Interleave: corefilters/Interleave.htm (Interleave)
