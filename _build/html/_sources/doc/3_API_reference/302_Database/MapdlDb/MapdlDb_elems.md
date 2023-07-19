# elems

````{py:property} property MapdlDb.elems

MAPDL database element interface.

Returns:
---------

`**DbElems**`

Examples
--------

Create a MAPDL database element instance.

```py
>>> from ansys.mapdl.core import launch_mapdl
>>> mapdl = launch_mapdl()
>>> elems = mapdl.db.elems
>>> print(elems)
MAPDL Database Elements
    Number of elements:          64
    Number of selected elements: 64
    Maximum element number:      64
```

Return the element information of element 1.

```py
>>> elems = mapdl.db.elems
>>> elem_info = elems.get(1)
```

Return the nodes belonging to the element.

```py
>>> elem_info.nodes
[2, 27, 37, 8]
```

Return the element data.

```py
>>> elem_info.elmdat
[1, 1, 1, 1, 0, 0, 14, 0, 0, 0]
```

````