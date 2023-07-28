# area_select

````{method} Geometry.area_select(items, sel_type='S', return_selected=False)

Select areas using a sequence of items.

Parameters:
----------

  *items* : [*sequence*](https://docs.python.org/3/glossary.html#term-sequence), *`str`* ,*`None`*
  : List, range, or sequence of integers of the areas you want to select. If `None` or `'NONE'`, no areas will be selected. If `'ALL'`, selects all areas.
  您要选择的 areas 的整数列表、范围或序列。如果为 `None` 或 `'NONE'`，则不会选择任何区域。如果为 `'ALL'`，则选择所有 areas。

  *sel_type* : *`str`*, *`optional`*
  : Selection type. May be one of the following:
  - `'S'`: Select a new set (default)
  - `'R'`: Reselect a set from the current set.
  - `'A'`: Additionally select a set and extend the current set.
  - `'U'`: Unselect a set from the current set.

  *return_selected* : *`bool`* , *`optional`*
  : Return the area numbers selected. Optional, and can be disabled for performance. Default `False`.\
  返回所选的 areas 编号。可选项，为提高性能可禁用。默认为 `False`。

Returns:
---------

  `list`
  : List of the selected areas if `return_selected=True`.

Examples
---------

Create a new selection of areas [1, 5, 10]

```python
>>> mapdl.geometry.area_select([1,5,10])
```

Create a new selection of areas from 1 through 20
```python
>>> mapdl.geometry.area_select(range(1, 21))
```


Unselect areas 1 through 20
```python
>>> mapdl.geometry.area_select(range(1, 21), sel_type='U')
```

Append to an existing selection of areas
```python
>>> mapdl.geometry.area_select([1, 2, 3], sel_type='A')
```

Reselect from the existing selection of areas
```python
>>> mapdl.geometry.area_select([3, 4, 5], sel_type='R')
```

Select no areas
```python
>>> mapdl.geometry.area_select(None)
```

Select all areas
```python
>>> mapdl.geometry.area_select('All')
```


````