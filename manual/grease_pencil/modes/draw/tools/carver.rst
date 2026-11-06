.. _tool-grease-pencil-draw-carver:
.. _bpy.ops.grease_pencil.stroke_carver:

***********
Carver Tool
***********

.. reference::

   :Mode:      Draw Mode
   :Tool:      :menuselection:`Toolbar --> Carver`

The Carver tool cuts strokes and fills along a freehand lasso, removing the portions inside it.
It can reshape a filled region, carve holes, or split a fill into separate islands.
Separate fill islands are assigned distinct fill IDs automatically.


Tool Settings
=============

.. _bpy.types.BrushGpencilSettings.use_active_layer_only:

Active Layer
   Restricts carving to the active layer. When disabled, all editable layers of the active object are affected.

.. _bpy.types.BrushGpencilSettings.use_keep_caps_eraser:

Keep Caps
   Preserves the stroke cap style at cut ends.
   When disabled, newly created stroke ends use :ref:`Flat caps <bpy.ops.grease_pencil.caps_set>`.


Usage
=====

Dragging with :kbd:`LMB` draws a lasso in the current view.
Releasing the mouse button applies the cut, removing stroke segments and filled areas inside the lasso.
The lasso is closed automatically.

When a material displays both strokes and fills, carving a hole also creates a stroke around the hole.
Cutting into such a shape from outside closes the fill along the new boundary.


Limitations
===========

Carving operates on poly curves. Non-poly curves near the lasso are automatically converted to poly curves,
and a warning is displayed. Curves belonging to the same fill may also be converted.
