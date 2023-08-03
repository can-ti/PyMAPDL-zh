# print

````{method} ansXpl.print(recname)

Print values of a given records, or all records (using `"*"`).

Parameters:
---------

  recname : *`str`*
  : Record of interest

  option : *`str`*
  : Options string.

Returns:
-------
  `str`
  : Response from MAPDL.


Examples
---------

```python
>>> xpl.open('file.full')
>>> print(xpl.print('DOFSBYNOD'))
=====      ANSYS File Xplorer : Print Block DOFSBYNOD
DOFSBYNOD :
Size : 3
       1         2         3
```


````