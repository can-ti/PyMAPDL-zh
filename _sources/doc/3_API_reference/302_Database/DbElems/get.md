# get

````{py:method} DbElems.get(ielm)

Get element attributes and nodes.

Parameters:
---------

  *ielm*: *`int`*
  : Element number. Should be 0 for key=11 for the following:

Returns:
-----------

  **`ansys.api.mapdl.v0.mapdl_db_pb2.getelmResponse`**
  : Element information containing the following attributes.
  - `ielm`: Element number
  - `elmdat`- Element data. Contains:
    - FIELD 0 : material reference number
    - FIELD 1 : element type number
    - FIELD 2 : real constant reference number
    - FIELD 3 : section number
    - FIELD 4 : element coordinate system
    - FIELD 5 : death flag (0 - alive, 1 - dead)
    - FIELD 6 : solid model reference
    - FIELD 7 : coded shape key
    - FIELD 8 : element number
    - FIELD 9 : base element number (applicable to reinforcing elements only)
  - `nnod` : Number of nodes
  - `nodes` : Node numbers belonging to the element

Examples
--------

Return the element information of element 1.

```python

>>> elems = mapdl.db.elems
>>> elem_info = elems.info(1)

```

Return the nodes belonging to the element.

```python

>>> elem_info.nodes
[2, 27, 37, 8]

```

Return the element data.

```python

>>> elem_info.elmdat
[1, 1, 1, 1, 0, 0, 14, 0, 0, 0]

```


````