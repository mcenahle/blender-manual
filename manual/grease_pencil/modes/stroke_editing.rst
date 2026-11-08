*********************
Grease Pencil Editing
*********************

These operations edit selected Grease Pencil points or strokes. They are
available in both Edit Mode and Draw Mode. Draw Mode provides them through the
*Stroke* menu.


.. _grease-pencil-editing-transform:

Transform
=========

Strokes can be edited by transforming the locations of points.


Move, Rotate & Scale
--------------------

.. reference::

   :Mode:      Edit Mode, Draw Mode
   :Tool:      :menuselection:`Toolbar --> Move, Rotate, Scale`
   :Shortcut:  :kbd:`G`, :kbd:`R`, :kbd:`S`

Like other elements in Blender, points and strokes can be moved, rotated, or
scaled as described in the
:doc:`Basic Transformations </scene_layout/object/editing/transform/introduction>`
section. :doc:`Proportional Editing </editors/3dview/controls/proportional_editing>`
is also available for these transformations.


Transform Snapping
------------------

Basic move, rotate, and scale transformations for selected points or strokes
can be performed using snapping. See
:doc:`Move, Rotate, Scale Basics </modeling/meshes/editing/mesh/transform/basic>`
for more information.


.. _grease-pencil-editing-mirror:

Mirror
======

.. reference::

   :Mode:      Edit Mode, Draw Mode
   :Menu:      :menuselection:`Grease Pencil --> Mirror` in Edit Mode, :menuselection:`Stroke --> Mirror` in Draw Mode
   :Shortcut:  :kbd:`Ctrl-M`

The *Mirror* tool behaves the same as with
:doc:`mesh vertices </modeling/meshes/editing/mesh/mirror>`.


.. _bpy.ops.grease_pencil.snap_to_grid:
.. _bpy.ops.grease_pencil.snap_to_cursor:
.. _bpy.ops.grease_pencil.snap_cursor_to_selected:

.. _grease-pencil-editing-snap:

Snap
====

.. reference::

   :Mode:      Edit Mode, Draw Mode
   :Menu:      :menuselection:`Grease Pencil --> Snap` in Edit Mode, :menuselection:`Stroke --> Snap` in Draw Mode
   :Shortcut:  :kbd:`Shift-S`

:doc:`Mesh snapping </editors/3dview/controls/snapping>` also works with
Grease Pencil components.


.. _bpy.ops.grease_pencil.duplicate_move:

Duplicate
=========

.. reference::

   :Mode:      Edit Mode, Draw Mode
   :Menu:      Edit: :menuselection:`Grease Pencil --> Duplicate`; Draw: :menuselection:`Stroke --> Duplicate`
   :Shortcut:  :kbd:`Shift-D`

Duplicates the selected elements without creating any connections with the
rest of the strokes (unlike *Extrude*, for example), and places the duplicate
at the location of the original elements.


.. _bpy.ops.grease_pencil.stroke_split:

Split
=====

.. reference::

   :Mode:      Edit Mode, Draw Mode
   :Menu:      Edit: :menuselection:`Grease Pencil --> Split`; Draw: :menuselection:`Stroke --> Split`
   :Shortcut:  :kbd:`V` in Edit Mode

The *Split* operator separates the selected portion of a curve from the rest,
creating a new, independent curve segment. This curve can then be moved or
altered without affecting the other curve.

- If a segment of the curve is selected, it is split off as a new curve that
  can be moved or edited independently.
- If only a single control point is selected, it is duplicated as a loose
  control point while the original remains attached to the rest of the curve.


.. _bpy.ops.grease_pencil.copy:

Copy
====

.. reference::

   :Mode:      Edit Mode, Draw Mode
   :Menu:      Edit: :menuselection:`Grease Pencil --> Copy`; Draw: :menuselection:`Stroke --> Copy`
   :Shortcut:  :kbd:`Ctrl-C`

Copies the selected points or strokes to the clipboard.


.. _bpy.ops.grease_pencil.paste:

Paste
=====

.. reference::

   :Mode:      Edit Mode, Draw Mode
   :Menu:      Edit: :menuselection:`Grease Pencil --> Paste`; Draw: :menuselection:`Stroke --> Paste`
   :Shortcut:  :kbd:`Ctrl-V`

Pastes Grease Pencil points or strokes from the internal clipboard to the
active layer.

Paste on Back :kbd:`Shift-Ctrl-V`
   Add pasted strokes behind all strokes.

Keep World Transform
   Keep the world transform of strokes from the clipboard unchanged.

In Draw Mode, the *Stroke* menu also provides *Paste Active* and *Paste by
Layer* for choosing where the pasted strokes are placed.


.. _grease-pencil-editing-active-layer:

Active Layer
============

.. reference::

   :Mode:      Edit Mode, Draw Mode
   :Menu:      Edit: :menuselection:`Grease Pencil --> Active Layer`; Draw: :menuselection:`Draw --> Active Layer`
   :Shortcut:  :kbd:`Y`

Selects the active layer.


.. _grease-pencil-editing-animation:

Animation
=========

.. reference::

   :Mode:      Draw Mode, Edit Mode
   :Menu:      Draw: :menuselection:`Draw --> Animation`; Edit: :menuselection:`Grease Pencil --> Animation`
   :Shortcut:  :kbd:`I`

The stroke animation operations are described in the
:doc:`Animation </grease_pencil/animation/tools>` section.


.. _grease-pencil-editing-interpolate-sequence:

Interpolate Sequence
====================

.. reference::

   :Mode:      Draw Mode, Edit Mode
   :Menu:      Draw: :menuselection:`Draw --> Interpolate Sequence`; Edit:
               :menuselection:`Grease Pencil --> Interpolate Sequence`

See :ref:`bpy.ops.grease_pencil.interpolate_sequence`.


Delete
======

.. reference::

   :Mode:      Edit Mode, Draw Mode
   :Menu:      :menuselection:`Grease Pencil --> Delete` in Edit Mode, :menuselection:`Stroke --> Delete` in Draw Mode
   :Shortcut:  :kbd:`X`, :kbd:`Delete` in Edit Mode; :kbd:`Delete` in Draw Mode

Opens a pop-up menu with operators to remove geometry from the Grease Pencil
object. The available delete options are the same in both modes and operate on
the current selection.

In Draw Mode, :kbd:`X` is reserved for swapping brush colors, so it is not a
delete shortcut. :kbd:`B` is reserved for Box Erase and is not a box-select
shortcut.

.. _bpy.ops.grease_pencil.delete:

Strokes
-------

Deletes the selected points. If deleting points leaves only a single point in a
stroke, the stroke will no longer be visible. If all points of a stroke are
removed, the entire stroke is deleted.


Only Strokes
------------

Deletes only the stroke (outline) component of the selected curves, preserving
any associated fill geometry.


Only Fills
----------

Deletes only the fill component of the selected curves, leaving the stroke
(outline) intact.


.. _bpy.ops.grease_pencil.dissolve:

Dissolve
--------

Dissolving removes points between other points and connects the remaining
points. :kbd:`Ctrl-X` opens a pop-up to choose the dissolve type.

Dissolve
   Deletes the selected points without splitting the stroke. The remaining
   points in the strokes stay connected.
Dissolve Between
   Deletes all the points between the selected points without splitting the
   stroke.
Dissolve Unselect
   Deletes all the points that are not selected in the stroke without splitting
   the stroke.


.. _grease-pencil-editing-clean-up:

Clean Up
========

These tools help to clean up degenerate geometry on the strokes.


.. _bpy.ops.grease_pencil.clean_loose:

Clean Loose Points
------------------

.. reference::

   :Mode:      Edit Mode, Draw Mode
   :Menu:      Edit: :menuselection:`Grease Pencil --> Clean Up --> Delete Loose Points`;
               Draw: :menuselection:`Stroke --> Clean Up --> Delete Loose Points`

Removes strokes with only a few points.

Limit
   The number of points to consider a stroke as loose.


.. _bpy.ops.grease_pencil.frame_clean_duplicate:

Delete Duplicate Frames
-----------------------

.. reference::

   :Mode:      Edit Mode, Draw Mode
   :Menu:      Edit: :menuselection:`Grease Pencil --> Clean Up --> Delete Duplicate Frames`;
               Draw: :menuselection:`Stroke --> Clean Up --> Delete Duplicate Frames`

Removes any duplicate keyframes.


.. _bpy.ops.grease_pencil.stroke_merge_by_distance:

Merge by Distance
-----------------

.. reference::

   :Mode:      Edit Mode, Draw Mode
   :Menu:      Edit: :menuselection:`Grease Pencil --> Clean Up --> Merge by Distance`;
               Draw: :menuselection:`Stroke --> Clean Up --> Merge by Distance`

Simplifies a stroke by merging the selected points that are closer than a specified distance to each other.
Note, unless using *Unselected*, selected points must be contiguous, else they will not be merged.

Merge Distance
   Sets the distance threshold for merging points.
Unselected
   Allows points in selection to be merged with unselected points.
   When disabled, selected points will only be merged with other selected ones.


.. _bpy.ops.grease_pencil.reproject:

Reproject Strokes
-----------------

.. reference::

   :Mode:      Edit Mode, Draw Mode
   :Menu:      Edit: :menuselection:`Grease Pencil --> Clean Up --> Reproject`;
               Draw: :menuselection:`Stroke --> Clean Up --> Reproject`

Sometimes you may have drawn strokes unintentionally in different locations in the 3D space
but they look right from a certain plane or from the camera view.
You can use Reproject to flatten all the selected strokes from a certain viewpoint.

Reprojected Type
   :Front: Reproject selected strokes onto the front plane (XZ).
   :Side: Reproject selected strokes onto the side plane (YZ).
   :Top: Reproject selected strokes onto the top plane (XY).
   :View: Reproject selected strokes onto the current view.
   :Surface: Reproject selected strokes onto the mesh surfaces.

      Surface Offset
         When Surface Mode is activated controls the stroke offset from the object.
   :Cursor: Reproject selected strokes onto 3D cursor rotation.

Keep Original
   Maintains the original strokes after applying the tool.

.. list-table::

   * - .. figure:: /images/grease-pencil_modes_edit_grease-pencil-menu_reproject-strokes-1.png
          :width: 200px

          Original drawing from the front view.

     - .. figure:: /images/grease-pencil_modes_edit_grease-pencil-menu_reproject-strokes-2.png
          :width: 200px

          Original drawing in the 3D Viewport.

     - .. figure:: /images/grease-pencil_modes_edit_grease-pencil-menu_reproject-strokes-3.png
          :width: 200px

          Strokes reprojected onto the front plane to fix strokes misalignment.

     - .. figure:: /images/grease-pencil_modes_edit_grease-pencil-menu_reproject-strokes-1.png
          :width: 200px

          Drawing after reprojection operation from the front view.


Stroke Menu
===========

The following options are available in the *Stroke* menu in both Edit Mode and
Draw Mode:

.. _bpy.ops.grease_pencil.set_uniform_thickness:

Set Uniform Thickness
=====================

.. reference::

   :Mode:      Edit Mode, Draw Mode
   :Menu:      :menuselection:`Stroke --> Set Uniform Thickness`

Makes the thickness equal for the entire stroke.

Thickness
   Thickness value to use on all points of the stroke.


.. _bpy.ops.grease_pencil.set_uniform_opacity:

Set Uniform Opacity
===================

.. reference::

   :Mode:      Edit Mode, Draw Mode
   :Menu:      :menuselection:`Stroke --> Set Uniform Opacity`

Makes the opacity equal for the entire stroke.

Opacity
   Opacity value to use on all points of the stroke.


.. _bpy.types.GPencilSculptSettings.use_scale_thickness:

Scale Thickness
===============

.. reference::

   :Mode:      Edit Mode, Draw Mode
   :Menu:      :menuselection:`Stroke --> Scale Thickness`

When enabled, scales the stroke thickness during scale transformations.

