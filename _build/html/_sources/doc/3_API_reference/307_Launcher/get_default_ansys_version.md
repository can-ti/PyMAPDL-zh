# get_default_ansys_version

````{function} ansys.mapdl.core.launcher.get_default_ansys_version()

Searches for ansys version within the standard install location and returns the version of the latest MAPDL version installed.\
在标准安装位置内搜索 ansys 路径，并返回已安装的最新 MAPDL 版本。

Returns:
-------

  *version* : *`float`*
  : Version float. For example, 21.1 corresponds to 2021R1.


Examples
----------

Within Windows

```python
>>> from ansys.mapdl.core.launcher import get_default_ansys
>>> get_default_ansys_version()
21.1
```

Within Linux

```python
>>> get_default_ansys_version()
21.1
```

````