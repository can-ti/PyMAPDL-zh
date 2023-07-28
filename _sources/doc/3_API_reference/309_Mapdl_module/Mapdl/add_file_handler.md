# add_file_handler

````{method} Mapdl.add_file_handler(filepath, append=False, level='DEBUG')

Add a file handler to the mapdl log. This allows you to redirect the APDL logging to a file.\
为 mapdl 日志添加文件处理程序。这样就可以将 APDL 日志重定向到一个文件。

Parameters:
--------------

  *filepath* : *`str`*
  : Filename of the log.

  *append* : *`bool`*
  : When `True`, appends to an existing log file. When `False`, overwrites the log file if it already exists.\
  为 `true` 时，附加到现有日志文件。当 `False` 时，如果日志文件已经存在，则将其覆盖。

  *level* : *`str`*
  : Log level. Must be one of: `'DEBUG'`, `'INFO'`, `'WARNING'`, `'ERROR'`.

Examples
---------

Start writing the log to a new file named “mapdl.log”\
开始将日志写入名为 "mapdl.log" 的新文件

```python
>>> mapdl.add_file_handler('mapdl.log')
```

````