# get_available_ansys_installations

````{function} ansys.tools.path.get_available_ansys_installations(supported_versions={191: '19.1', 192: '19.2', 193: '19.3', 194: '19.4', 195: '19.5', 201: '2020R1', 202: '2020R2', 211: '2021R1', 212: '2021R2', 221: '2022R1', 222: '2022R2', 231: '2023R1', 232: '2023R2'})

Return a dictionary of available Ansys unified installation versions with their base paths.\
返回可用的 Ansys 统一安装版本及其基本路径的字典。

Returns:
-------

  `dict` : [int:`str`]
  : Return all Ansys unified installations paths in Windows.\
  返回 Windows 中所有 Ansys 统一安装路径。

Notes
--------

On Windows, It uses the environment variable `AWP_ROOTXXX`.\
在 Windows 系统中，它使用环境变量 `AWP_ROOTXXX`。

The student versions are returned at the end of the dict and with negative value for the version.\
学生版本在结果的末尾返回，版本的值为负。

Examples
-----------

```python
>>> from ansys.tools.path import get_available_ansys_installations
>>> get_available_ansys_installations()
{222: 'C:\Program Files\ANSYS Inc\v222',
 212: 'C:\Program Files\ANSYS Inc\v212',
 -222: 'C:\Program Files\ANSYS Inc\ANSYS Student\v222'}
```

Return all installed Ansys paths in Linux.

```python
>>> get_available_ansys_installations()
{194: '/usr/ansys_inc/v194',
 202: '/usr/ansys_inc/v202',
 211: '/usr/ansys_inc/v211'}
```


````