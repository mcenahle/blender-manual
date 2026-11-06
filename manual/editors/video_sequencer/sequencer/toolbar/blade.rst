.. _tool-blade:

**********
Blade Tool
**********

.. reference::

   :Editor:    Video Sequencer
   :Tool:      :menuselection:`Toolbar --> Blade`

The Blade tool cuts a strip in two. It first shortens the strip so it only shows the content
up to the cut point, then adds a second strip that shows the content after the cut point.

The tool supports both point-based cuts and a box gesture for quickly removing unwanted sections of strips.

Holding :kbd:`C` in the timeline temporarily activates Blade.
Releasing :kbd:`C` restores the previous tool.
A line marks the cut position, and tooltips show the affected frame values.
While dragging a box, a highlighted region shows the area to remove.
With :ref:`Preview Edit Point <bpy.types.SpaceSequenceEditor.show_transform_preview>` enabled,
hovering over strips also displays the cut frame in the Preview.


Usage
=====

- Click a strip at the time point where it should be split.
- Click and drag to draw a box. All strip content inside the box is cut out and removed.

Holding :kbd:`Shift` while clicking cuts across all channels at that frame.
Holding :kbd:`Alt` while clicking or dragging prevents cuts from propagating to connected strips.

When using the box gesture, all strip content inside the box area is deleted.
With *Remove Gaps* enabled, strips that follow the removed section are moved backward in time
to close the gap (ripple behavior).

When rippling, the behavior is applied to all channels that intersect the box area.
Channels that are not covered by the box remain unchanged, allowing other strips
to keep their relative timing if desired.

If the box starts at the beginning or end of a strip, the amount of ripple is
determined by the distance from the strip handle to the time-side of the box.
When the box spans gaps between strips, those gaps can also be removed when rippling is enabled.


Tool Settings
=============

Settings are grouped into *Split* for click cuts and *Box Blade* for box gestures.
Each group has its own split type and selection settings.
In the tool header, additional settings are available in the :menuselection:`...` popover.

Type :guilabel:`Split` :guilabel:`Box Blade`
   Determines whether cuts preserve access to trimmed content.

   :Soft:
      After splitting, it is still possible to restore the cut content in the new strips
      by dragging their handles.
   :Hard:
      After splitting, it is not possible to restore the cut content by dragging handles.
      However, the content can still be restored by adjusting the
      :ref:`Hold Offset <sequencer-duration-hard>` in the Sidebar.

All Channels :guilabel:`Split`
   Cuts strips across all channels at the cut frame rather than only the channel under the pointer.

Only Selected :guilabel:`Split` :guilabel:`Box Blade`
   Restricts cuts to selected strips. Cuts do not propagate to unselected connected strips.

Remove Gaps :guilabel:`Box Blade`
   In box blade mode, close gaps between cut strips, rippling later strips backward in time.
   Hold :kbd:`Shift` before dragging to temporarily disable this option and keep the gap.

Ignore Connections :guilabel:`Split` :guilabel:`Box Blade`
   Does not propagate the cut to connected strips.
   Unavailable when *Only Selected* is enabled, or for click cuts when *All Channels* is enabled.
