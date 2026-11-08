
******************
Grease Pencil Menu
******************

Transform, duplication, clipboard, and deletion operations are documented in
:doc:`Grease Pencil Editing </grease_pencil/modes/stroke_editing>`.


:ref:`Transform <grease-pencil-editing-transform>`
==================================================


Transform Tools
---------------

.. reference::

   :Mode:      Edit Mode
   :Menu:      :menuselection:`Grease Pencil --> Transform`
   :Tool:      :menuselection:`Toolbar --> Bend/Shear`

The *Bend*, *Shear*, *To Sphere*, *Extrude*, and *Shrink Fatten* transform tools
are described in the :doc:`Editing tools </grease_pencil/modes/edit/tools/index>`
section.


:ref:`Mirror <grease-pencil-editing-mirror>`
============================================


:ref:`Snap <grease-pencil-editing-snap>`
========================================


:ref:`Active Layer <grease-pencil-editing-active-layer>`
========================================================


:ref:`Animation <grease-pencil-editing-animation>`
==================================================


:ref:`Interpolate Sequence <grease-pencil-editing-interpolate-sequence>`
========================================================================


:ref:`Duplicate <bpy.ops.grease_pencil.duplicate_move>`
=======================================================


:ref:`Split <bpy.ops.grease_pencil.stroke_split>`
=================================================


:ref:`Copy <bpy.ops.grease_pencil.copy>`
========================================


:ref:`Paste <bpy.ops.grease_pencil.paste>`
==========================================


.. _grease-pencil-menu-show-hide:

Show/Hide
=========

Contains operators to adjust the visibility of points and strokes in the viewport.


Show All Layers
---------------

.. reference::

   :Mode:      Edit Mode
   :Menu:      :menuselection:`Grease Pencil --> Show/Hide --> Show All Layers`
   :Shortcut:  :kbd:`Alt-H`

Shows all Grease Pencil :doc:`layers </grease_pencil/properties/layers>`.


.. _bpy.ops.grease_pencil.layer_hide:

Hide Active Layer
-----------------

.. reference::

   :Mode:      Edit Mode
   :Menu:      :menuselection:`Grease Pencil --> Show/Hide --> Hide Active Layer`
   :Shortcut:  :kbd:`H`

Hides the active Grease Pencil :doc:`layers </grease_pencil/properties/layers>`.


Hide Inactive Layers
--------------------

.. reference::

   :Mode:      Edit Mode
   :Menu:      :menuselection:`Grease Pencil --> Show/Hide --> Hide Active Layer`
   :Shortcut:  :kbd:`Shift-H`

Hides all Grease Pencil :doc:`layers </grease_pencil/properties/layers>` except the active layer.


.. _bpy.ops.grease_pencil.separate:

Separate
========

.. reference::

   :Mode:      Edit Mode
   :Menu:      :menuselection:`Grease Pencil --> Separate`
   :Shortcut:  :kbd:`P`

Separate different elements into new Grease Pencil objects based on specific criteria.

Selection
   Separates the selected points or strokes into a new object.
By Material
   Separates the geometry by creating a new object for each material.
By Layer
   Separates the geometry by creating a new object for each layer.
   See :doc:`2D Layers </grease_pencil/properties/layers>` for more information.


:ref:`Clean Up <grease-pencil-editing-clean-up>`
================================================

The *Clean Up* operations that are also available in Draw Mode are documented
in the :doc:`Grease Pencil Editing </grease_pencil/modes/stroke_editing>` section.


.. _bpy.ops.grease_pencil.outline:

Outline
=======

.. reference::

   :Mode:      Edit Mode
   :Menu:      :menuselection:`Grease Pencil --> Outline`

The *Outline* operator converts selected Grease Pencil strokes into closed perimeter shapes.
It creates new strokes around the outer boundary of the original stroke,
effectively generating a filled outline with adjustable thickness.

View
   Defines the projection method used to generate the outline:

   :View: Use the current viewport perspective as the projection plane.
   :Front: Use the X-Z axes as the projection plane (front view).
   :Side: Use the Y-Z axes as the projection plane (side view).
   :Top: Use the X-Y axes as the projection plane (top view).
   :Camera: Use the active camera's perspective as the projection plane.
Radius
   Sets the thickness of the outline on both sides of the original stroke.
   Higher values result in a wider perimeter.
Offset Factor
   Scales the stroke outline inward or outward.
   - Positive values push the perimeter outward.
   - Negative values pull it inward.
   - A value of 0 centers the perimeter on the original stroke.
Corner Subdivisions
   Number of subdivisions used to smooth corners at stroke endpoints and joints.
   Higher values result in smoother corners but increase stroke complexity.

.. list-table::

   * - .. figure:: /images/grease-pencil_modes_edit_stroke-menu_outline-1.png
          :width: 320px

          Original stroke.

     - .. figure:: /images/grease-pencil_modes_edit_stroke-menu_outline-2.png
          :width: 320px

          Stroke after applying the *Outline* operator.


:ref:`Delete <bpy.ops.grease_pencil.delete>`
============================================

Delete operations that are also available in Draw Mode are documented in the
:doc:`Grease Pencil Editing </grease_pencil/modes/stroke_editing>` section.


Delete Active Keyframe (Active Layer)
-------------------------------------

.. reference::

   :Mode:      Edit Mode
   :Menu:      :menuselection:`Grease Pencil --> Delete --> Delete Active Keyframe (Active Layer)`

Deletes all the strokes at the current frame in the active layer.


Delete Active Keyframes (All Layers)
------------------------------------

.. reference::

   :Mode:      Edit Mode
   :Menu:      :menuselection:`Grease Pencil --> Delete --> Delete Active Keyframes (All Layers)`
   :Shortcut:  :kbd:`Shift-Delete`

Deletes all the strokes at the current frame in all layer.
