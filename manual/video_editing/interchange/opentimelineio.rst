
**************
OpenTimelineIO
**************

:abbr:`OpenTimelineIO (OTIO)` is an open-source format for exchanging
video editing timelines between applications.

Blender supports importing and exporting OpenTimelineIO (``.otio``) files,
allowing edits to be transferred between the Video Sequencer and other
compatible video editing applications.

OpenTimelineIO stores the structure of an edit, including clip timing,
track organization, and references to source media. The media files
themselves are not embedded in the exported timeline.

.. seealso::

   `OpenTimelineIO Documentation <https://opentimelineio.readthedocs.io/>`__


Import
======

Imports an OpenTimelineIO file into the Video Sequencer, converting supported
timeline elements into strips.

The imported timeline preserves the timing and organization of the original edit,
including track names, channel assignments, and mute and lock states where supported.

The timeline's frame rate and global start time are used to set the scene's
frame rate and start frame.

If the current Sequencer scene already contains strips, a new scene is created
for the imported timeline to avoid modifying the existing edit.

When importing while a Video Sequencer is visible, Blender automatically switches to
the destination scene. Otherwise, the import is performed without switching
scenes, and the destination scene is reported.

Multiple OpenTimelineIO files can be imported at once.
Files can also be imported by dragging and dropping them into the Video Sequencer.

.. note::

   The original media files must remain accessible for the imported
   strips to display correctly.


Metadata
--------

Any Blender-specific metadata previously exported is restored to the corresponding
scene and strip properties where supported. This includes information needed to
reconstruct the original Video Sequencer timeline, such as channel assignments.

Metadata from other editing applications is interpreted where possible.
Unrecognized metadata is preserved as custom properties on the scene or strips,
allowing it to be retained when exporting the timeline again.

Some timeline elements and application-specific features may not be fully
supported when importing files created by other video editing applications.


Export
======

Exports the Video Sequencer timeline to an OpenTimelineIO file,
allowing the edit to be transferred to other compatible video editing applications.

The exported file contains the timeline structure, strip timing,
track organization, and references to source media.

Video Sequencer channels containing both video and audio strips are exported
as separate video and audio tracks. The original channel assignments are
stored as metadata so they can be restored when importing the file back into Blender.


Metadata
--------

Blender-specific strip properties are stored as metadata in the exported file.
This allows information that is not directly supported by OpenTimelineIO
to be preserved when importing the timeline back into Blender.

Metadata from other editing applications that was preserved during import
is also included when exporting, allowing it to be retained across multiple
import and export operations.


Options
-------

DaVinci Resolve Metadata
   Exports additional metadata recognized by DaVinci Resolve to improve
   compatibility when importing the timeline into that application.

   This metadata is used to represent certain timeline elements that
   are not directly supported by OpenTimelineIO.
   See :ref:`otio-davinci-resolve` for the supported properties.


Limitations
===========

Export
------

The following are not exported yet, but should receive some support in the future:

- Mask, Movie Clip, Multicam, and Compositor strips.
  These strips are skipped and a warning is reported.
- Transitions whose input strips are on different channels.
- Drivers, and animation other than the keyframes listed under :ref:`otio-davinci-resolve`.
  Other animated properties are exported with their current value.
- Retiming keys.
- Empty channels, including their names.
- Channel lock state, unless export metadata is enabled.
- Scene settings other than the frame rate and start frame.
- Add, Subtract, Multiply, Alpha Over, Alpha Under, and Color Mix effect strips.

The following are exported, but other applications cannot read them correctly as they
are features unique to the Blender VSE:

- Scene strips with *Input* set to *Camera* are seen as clips with missing media.
  On import, they are properly restored if a scene with the same name exists in the blendfile.
- Image sequences with arbitrary or nonsequential frame numbering are seen as clips with missing media.
- Strip modifiers and some strip properties are only stored as Blender-specific metadata.

.. note::

   Editing or reexporting the timeline in another application
   may discard the Blender-specific metadata needed to restore these strips.
   However, OpenTimelineIO suggests applications to preserve metadata they don't use, so
   this should be reported to that application's developers.

Import
------

The following are not imported yet, but should receive some support in the future:

- OpenTimelineIO bundles (``.otioz``, ``.otiod``) and files containing more than one timeline.
- Clips with missing media, or media that is not a local file.
  These clips are skipped and a warning is reported.
- Generator clips that Blender does not recognize.
- Clip effects, except time warps and effects exported from Blender.
  Linear time warps are imported as Speed strips, and negative time warps reverse the strip.
- Transitions that are not between two clips, such as fades from black.
- Markers on clips and tracks. Only markers on the timeline are imported, without their color or duration.

.. _otio-davinci-resolve:

DaVinci Resolve
---------------

When *DaVinci Resolve Metadata* is enabled, the following strip properties are exported
with the custom DaVinci Resolve metadata that it recognizes:

- Position, scale, rotation, origin, flip, and crop.
- Opacity and blend mode. Note that the Replace, Cross, Gamma Cross, and Alpha Under blend modes are not supported.
- Volume and pan of sound strips.
- Color of color strips.
- Text, size, color, and location of text strips.
- Adjustment Layer strips.
- Wipe angle. All wipe types are exported as an edge wipe.
- Channel lock state.
- Connected strips. However, note that DaVinci Resolve only keeps connections between the video and audio
  of the same clip, and does not support arbitrary connections in its OTIO metadata.
- Keyframes for position, scale, rotation, crop, opacity, volume, pan, and wipe angle
  (but not interpolation or handles).