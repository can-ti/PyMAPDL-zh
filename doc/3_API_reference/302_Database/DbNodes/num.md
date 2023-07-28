# num

````{py:method} DbNodes.num(selected=False)

Number of nodes.

Parameters:
-----------

  *selected*: *`bool`*,**`optional`**
  : Return either the number of selected nodes of the total number of nodes.\
  返回所选择的节点数量或节点总数。

Returns:
---------

  `int`
  : Number of nodes.

Examples
----------

Get the number of selected nodes.

```python

>>> nodes = mapdl.db.nodes
>>> nodes.num(selected=True)
425

```

````
