# list_files

````{method} MapdlGrpc.list_files(refresh_cache=True)

List the files in the working directory of MAPDL.

Parameters:
---------

  refresh_cache : *`bool`* , *`optional`*
  : If local, refresh local cache by querying MAPDL for its current path.\
  如果是本地缓存，则通过查询 MAPDL 的当前路径来刷新本地缓存。


Returns:
-------

  `list`
  : List of files in the working directory of MAPDL.

Examples
----------


```python
>>> files = mapdl.list_files()
>>> for file in files: print(file)
file.lock
file0.bat
file0.err
file0.log
file0.page
file1.err
file1.log
file1.out
file1.page
```







````