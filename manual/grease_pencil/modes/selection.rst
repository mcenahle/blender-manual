*******************************
Selecting Grease Pencil Strokes
*******************************

Grease Pencil selection tools can be used in Draw, Edit, Sculpt, and Vertex Paint
Mode. The tools use the same interaction as the general
:doc:`selection tools </interface/selecting>`.


Selection Tools
===============

.. reference::

   :Mode:      Draw Mode, Edit Mode, Sculpt Mode, Vertex Paint Mode
   :Tool:      3D Viewport Toolbar

:ref:`Tweak <tool-select-tweak>`
   Select strokes by clicking them, or move selected strokes by dragging.

:ref:`Select Box <tool-select-box>`
   Select strokes inside a rectangular region.

:ref:`Select Circle <tool-select-circle>`
   Select strokes by painting over them with a circular region.

:ref:`Select Lasso <tool-select-lasso>`
   Select strokes inside a freeform region.

In Draw Mode, these tools select complete strokes. Selection is shown in the
viewport while a selection tool is active. In Edit Mode, the selection can be
restricted to points, strokes, or segments with the :doc:`Select Mode
</grease_pencil/modes/edit/selecting>` controls.

In Sculpt and Vertex Paint Mode, selection can be used as a mask to restrict
the effect of the active tool. See the mode-specific introductions for more
information about selection masks.


Shared Selection Operators
==========================

The following operators are available in Draw and Edit Mode. In Draw Mode,
they operate on complete strokes.

.. _bpy.ops.grease_pencil.select_all:

Select All/None/Invert
----------------------

.. reference::

   :Mode:      Draw Mode, Edit Mode
   :Menu:      :menuselection:`Select --> All`, :menuselection:`Select --> None`, :menuselection:`Select --> Invert`

Selects all elements, deselects all elements, or inverts the current selection.
These options have the same meaning and behavior as in
:doc:`Object Mode </scene_layout/object/selecting>`.


.. _bpy.ops.grease_pencil.select_by_stroke_type:

By Stroke Type
--------------

.. reference::

   :Mode:      Draw Mode, Edit Mode
   :Menu:      :menuselection:`Select --> By Stroke Type`

Selects curves based on whether they are strokes or fills.

Type
   :Stroke: Select all stroke curves (outlines).
   :Fill: Select all fill curves (enclosed filled shapes).

Deselect
   If enabled, matching curves are deselected instead of selected.


.. _bpy.ops.grease_pencil.select_fill:

Select Fill
-----------

.. reference::

   :Mode:      Draw Mode, Edit Mode
   :Menu:      :menuselection:`Select --> Select Fill`
   :Shortcut:  :kbd:`Ctrl-L` in Edit Mode

Selects all curves that belong to the same fill region as the active curve.

Grease Pencil fills can be composed of multiple boundary curves. This operator
expands the current selection to include all curves that define the same
enclosed fill area.

