# info

````{method} ansXpl.info(recname, option='')

Gives details on a specific record, or all records (using `"*"`)

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
>>> print(xpl.info('NGPH'))
=====      ANSYS File Xplorer : Information about Block NGPH
::NGPH                 Size =      6.289 KB
         - Record Size   : 81
         - Data type     : integer values
```



````