# next

````{py:method} DbElems.next()

Return the number of the next selected element.

You must first call `DbElems.first()`.

Returns:
---------

  `int`
  : The next selected element number. Returns 0 if there are no more nodes.

Examples
-----------

Call `DbElems.first()` first.

```python

>>> elems = mapdl.db.elems
>>> elems.first()
1

```

Then get the next node.

```python

>>> elems.next()
2

```

````