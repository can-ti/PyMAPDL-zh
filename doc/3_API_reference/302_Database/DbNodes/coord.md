# coord

````{method} DbNodes.coord(inod)

Return the location of a node.

Parameters:
----------

  *inod*: `int`
  : Node number.

Returns:
------------

  `int`
  : Selection status:
  - 0 - node is selected
  - 1 - node is not defined
  -1 - node is unselected

  `tuple`
  : Coordinates (first 3 values) and rotation angles (last 3 values).\
  坐标（前 3 个值）和旋转角度（后 3 个值）。

Examples
--------

Return the selection status and the coordinates of node 22.

```python
>>> nodes = mapdl.db.nodes
>>> sel, coord = nodes.coord(22)
>>> coord
(1.0, 0.5, 0.0, 0.0, 0.0, 0.0)
```


````