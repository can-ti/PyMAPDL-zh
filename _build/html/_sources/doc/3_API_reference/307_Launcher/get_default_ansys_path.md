# get_default_ansys_path

````{function} ansys.mapdl.core.launcher.get_default_ansys_path()

Searches for ansys path within the standard install location and returns the path of the latest MAPDL version installed.\
在标准安装位置内搜索 ansys 路径，并返回已安装的最新 MAPDL 版本的路径。

Returns:
-------

  *ansys_path* : *`str`*
  : Full path to ANSYS executable.


Examples
----------

Within Windows

```python
>>> from ansys.mapdl.core.launcher import get_default_ansys
>>> get_default_ansys_path()
'C:/Program Files/ANSYS Inc/v211/ANSYS/bin/winx64/ansys211.exe'
```

Within Linux

```python
>>> get_default_ansys_path()
'/usr/ansys_inc/v211/ansys/bin/ansys211'
```

````