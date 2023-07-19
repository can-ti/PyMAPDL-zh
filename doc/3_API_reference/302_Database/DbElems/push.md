# push

````{py:method} DbElems.push(item,elmdat,nodes)

Push an element into the database.

Examples
-------

Push a new linear hexahedron to MAPDL. This assumes that element type 1 has been set to SOLID185 with `mapdl.etype(1, "SOLID185")`.\
向 MAPDL 输入一个新的线性六面体。假设单元类型 1 已通过 `mapdl.etype(1, "SOLID185")` 设置为 SOLID185。

```python

>>> elems = mapdl.db.elems
>>> elems.push(
    1,
    [1, 1, 1, 1, 0, 0, 1, 0, 0, 0],
    [1, 2, 3, 4, 5, 6, 7, 8],
)

```

````