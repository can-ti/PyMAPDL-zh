# num

````{py:method} DbElems.num(selected=False)

Number of elements.

Parameters:
-----------

  *selected*: *`bool`*,**`optional`**
  : Return either the number of selected elements of the total number of elements.\
  返回所选择的单元数量或单元总数。

Returns:
---------

  `int`
  : Number of elements. Set `selected` to `True` to include selection status.

Examples
----------

Get the number of selected elements.

```python

>>> elems = mapdl.db.elems
>>> elems.num(selected=True)
425

```

````
