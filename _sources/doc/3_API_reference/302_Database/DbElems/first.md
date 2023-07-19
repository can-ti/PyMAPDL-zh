# first

````{method} DbElems.first(ielm=0)

获取第一个单元的编号。

This starts at `inod`, defaults to the first element in the model.\
从 `inod` 开始，默认为模型中的第一个单元。

Parameters:
------------

  *ielm*: *`int`*,***`optional`***
  : The first element number to consider as the “first element”.\
  作为 "第一格单元"的第一个单元编号。

Returns:
--------

   `int`
   : The first element number after `ielm`.

Examples
----------

Return the first selected element.

```python
>>> elems = mapdl.db.elems
>>> elems.first()
1
```

Return the first element after element 10.

```python
>>> elems.first(ielm=10)
11
```


````