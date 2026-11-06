.. _bpy.ops.mesh.fit_edge_loops_to_annotation:

****************************
Fit Edge Loops To Annotation
****************************

.. reference::

   :Mode:      Edit Mode
   :Menu:      :menuselection:`Mesh --> Transform --> Fit Edge Loops To Annotation`

The *Fit Edge Loops To Annotation* operator reshapes selected edge loops to follow
:doc:`annotation strokes </interface/annotate_tool>`.
It moves existing vertices without adding or removing geometry.

Guide strokes can be drawn in the 3D Viewport using the *Annotate* tool with *Placement*
set to *3D Cursor* or *Surface*. The operator then fits the edges selected in Edit Mode to these strokes.
Only 3D strokes with at least two points from the active annotation layer's active frame are used.
Strokes drawn with *View* placement are ignored.

When several edge loops and strokes are present, strokes that have not yet been assigned
to a loop are preferred. Among equally used strokes, the stroke whose center is closest
to the loop's center is chosen. A stroke can be reused when there are more loops than strokes.

If no usable annotation strokes are available, a straight line between the first and last
vertices of each edge chain is used instead.


Options
=======

Factor
   Controls how far the vertices move toward their target positions.
   A value of zero leaves the vertices unchanged; a value of one applies the full adjustment.

Method
   Determines how vertices are fitted to the stroke.

   :Spread:
      Distributes vertices along the entire stroke while preserving their relative spacing along the edge loop.
   :Spread Evenly:
      Distributes vertices at equal distances along the entire stroke.
   :Project:
      Projects vertices onto the stroke along connected unselected edges that share faces with the selected edges.
      If no suitable projection is found, the vertex normal is used instead.
      The stroke must lie close to these projection lines; vertices without a suitable projection remain unchanged.

Delete Strokes
   Removes the usable 3D annotation strokes from the active layer's active frame after applying the operator.

Lock
   Prevents changes to vertex coordinates along the enabled X, Y, or Z axes in the object's local space.
