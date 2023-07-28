# line_select

````{method} Geometry.line_select(items, sel_type='S', return_selected=False)

Select lines using a sequence of items.

Parameters:
----------

  *items* : [*sequence*](https://docs.python.org/3/glossary.html#term-sequence) or *`None`*
  : List, range, or sequence of integers of the lines you want to select. If `None` or `'NONE'`, no lines will be selected. If `'ALL'`, selects all lines.
  您要选择的 lines 的整数列表、范围或序列。如果为 `None` 或 `'NONE'`，则不会选择任何 lines。如果为 `'ALL'`，则选择所有 lines。

  *sel_type* : *`str`*, *`optional`*
  : Selection type. May be one of the following:
  - `'S'`: Select a new set (default)
  - `'R'`: Reselect a set from the current set.
  - `'A'`: Additionally select a set and extend the current set.
  - `'U'`: Unselect a set from the current set.

  *return_selected* : *`bool`* , *`optional`*
  : Return the line numbers selected. Optional, and can be disabled for performance. Default `False`.\
  返回所选的 lines 编号。可选项，为提高性能可禁用。默认为 `False`。

Returns:
---------

  `list`
  : List of line numbers if `return_selected=True`.

Examples
---------

Create a new selection of lines [1, 5, 10]

```python
>>> mapdl.geometry.line_select([1,5,10])
```

Create a new selection of lines from 1 through 20
```python
>>> mapdl.geometry.line_select(range(1, 21))
```


Unselect lines 1 through 20
```python
>>> mapdl.geometry.line_select(range(1, 21), sel_type='U')
```

Append to an existing selection of lines
```python
>>> mapdl.geometry.line_select([1, 2, 3], sel_type='A')
```

Reselect from the existing selection of lines
```python
>>> mapdl.geometry.line_select([3, 4, 5], sel_type='R')
```

Select no lines
```python
>>> mapdl.geometry.line_select(None)
```

Select all lines
```python
>>> mapdl.geometry.line_select('All')
```


````