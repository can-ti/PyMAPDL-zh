# log_to_file

````{method} Logger.log_to_file(filename='pymapdl.log', level=10)

Add file handler to logger.\
为日志程序添加文件处理程序。

Parameters:
---------

  *filename* : *`str`* , *`optional`*
  : Name of the file where the logs are recorded. By default `'pymapdl.log'`.\
  记录日志的文件名。默认为 `'pymapdl.log'`。

  *level* : *`str`* , *`optional`*
  : Level of logging. By default `'DEBUG'`.\
  日志记录级别。默认为"'DEBUG'"。

Examples
----------

Write to `pymapdl.log` in the current working directory.\
写入当前工作目录下的 `pymapdl.log`。

```python
>>> from ansys.mapdl.core import LOG
>>> import os
>>> file_path = os.path.join(os.getcwd(), 'pymapdl.log')
>>> LOG.log_to_file(file_path)
```








````