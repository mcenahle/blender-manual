.. _bpy.ops.mesh.curve_edge_loops_between_selected:

*********************************
Curve Edge Loops Between Selected
*********************************

.. reference::

   :Mode:      Edit Mode
   :Menu:      :menuselection:`Mesh --> Transform --> Curve Edge Loops Between Selected`

The *Curve Edge Loops Between Selected* operator reshapes unselected vertices along edge loops
to follow a curve defined by selected vertices. The selected vertices remain fixed as control points.
The operator moves existing vertices without adding or removing geometry.

Control vertices can be selected at intervals along an edge loop or wire chain.
Selecting entire edge loops uses those vertices as control points for the loops running across them.
This allows the shape between selected loops to be adjusted while keeping the selected loops unchanged.

With *Extend Loop* disabled, only vertices between the outermost selected control vertices are affected.


Operator Options
================

Factor
   Strength of the adjustment. A value of zero leaves the mesh unchanged;
   a value of one moves affected vertices fully to the calculated curve.

Clamp Elevation
   Restricts movement relative to each vertex's normal.
   This restriction does not apply to wire vertices, which have no face normal.

   :None: Allows movement in either direction.
   :Only Raise:
      Prevents adjustments that move a vertex against its normal, allowing outward adjustments.
   :Only Lower:
      Prevents adjustments that move a vertex along its normal, allowing inward adjustments.

Extend Loop
   Includes vertices beyond the outermost selected control vertices.
   For open chains, the chain endpoints are also kept fixed and used as control points.
   For closed loops with a large unselected gap, the affected region is limited around the selection
   to prevent the loop from collapsing.

Space Evenly
   Calculates the curve using evenly spaced vertex parameters rather than the existing distances along the loop.
   Selected control vertices remain fixed.

Lock
   Prevents changes along the enabled X, Y, or Z axes in the object's local space.

Interpolation
   Determines the shape of the curve between control vertices.

   :Cubic: Uses a cubic spline to create a smooth curve through the control vertices.
   :Linear: Uses straight segments between control vertices.
