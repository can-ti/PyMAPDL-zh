# push

````{py:method} DbNodes.push(inod, x, y, z, xang=None, yang=None, zang=None)

Push a single node into the DB.


Parameters：
----------

  *inod* ： *`int`*
  : Node number.

  *x* : *`float`*
  : X coordinate.
  
  *y* : *`float`*
  : Y coordinate.
  
  *z* : *`float`*
  : Z coordinate.
  
  *xang* : *`float`*, *`optional`*
  : X angle.
  
  *yang* : *`float`*, *`optional`*
  : Y angle.
  
  *zang* : *`float`*, *`optional`*
  : Z angle.



Examples
-------

Update node 1 to have coordinates (10.0, 20.0, 30.0).

```python

>>> nodes = mapdl.db.nodes
>>> nodes.push(1, 10, 20, 30)
>>> sel, coord = nodes.coord(1)
coord
(10.0, 20.0, 30.0, 0.0, 0.0, 0.0)

```

````