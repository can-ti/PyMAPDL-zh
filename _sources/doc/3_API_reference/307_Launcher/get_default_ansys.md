# get_default_ansys

````{function} ansys.mapdl.core.launcher.get_default_ansys()

Searches for ansys path within the standard install location and returns the path and version of the latest MAPDL version installed.\
在标准安装位置内搜索 ansys 路径，并返回已安装的最新 MAPDL 版本的路径和版本。

Returns:
-------

  *ansys_path* : *`str`*
  : Full path to ANSYS executable.

  *version* : *`float`*
  : Version float. For example, 21.1 corresponds to 2021R1.


Examples
----------

Within Windows

```python
>>> from ansys.mapdl.core.launcher import get_default_ansys
>>> get_default_ansys()
'C:/Program Files/ANSYS Inc/v211/ANSYS/bin/winx64/ansys211.exe', 21.1
```

Within Linux

```python
>>> get_default_ansys()
(/usr/ansys_inc/v211/ansys/bin/ansys211, 21.1)
```

````