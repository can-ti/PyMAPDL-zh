# Parameters

````{class} ansys.mapdl.core.parameters.Parameters(mapdl)

Collection of MAPDL parameters.

Notes
------

See [Setting and retrieving parameters](https://mapdl.docs.pyansys.com/version/stable/user_guide/parameters.html#ref-parameters) for additional notes.\
有关其他说明，请参见{doc}`设置和检索参数 <../1_User_guide/107_设置和检索参数>`。

Examples
--------

Simply list all parameters except for MAPDL MATH parameters.\
只列出除 MAPDL MATH 参数以外的所有参数。

```python
>>> mapdl.parameters
ARR                              : ARRAY DIM (3, 1, 1)
PARM_FLOAT                       : 20.0
PARM_INT                         : 10.0
PARM_LONG_STR                    : "stringstringstringstringstringst"
PARM_STR                         : "string"
PORT                             : 50052.0
```

Get a parameter\
获取一个参数

```python
>>> mapdl.parameters['PARM_FLOAT']
20.0
```

Get an array parameter

```python
>>> mapdl.parameters['ARR']
array([1., 2., 3.])
```

Methods
-------

```{table}

| | | |
|---|---|---|
| {doc}`Parameters.copy() <../Parameters/copy>` | Return a shallow copy of the dictionary. | 返回字典的浅层副本。 |
| {doc}`Parameters.items() <../Parameters/items>` | Return a view object that contains the key-value pairs in the dictionary. | 返回包含字典中键值对的视图对象。 |
| {doc}`Parameters.keys() <../Parameters/keys>` | Return a view object that contains the keys in the dictionary. | 返回一个视图对象，其中包含字典中的键。 |
| {doc}`Parameters.values() <../Parameters/values>` | Return a view object that contains the values in the dictionary. | 返回一个视图对象，其中包含字典中的值。 |


```



Attributes
----------

```{table}

| | | |
|---|---|---|
| {doc}`Parameters.csys <../Parameters/csys>` | Active coordinate system |  |
| {doc}`Parameters.dsys <../Parameters/dsys>` | Active display coordinate system |  |
| {doc}`Parameters.esys <../Parameters/esys>` | Active element coordinate system |  |
| {doc}`Parameters.material <../Parameters/material>` | Active material |  |
| {doc}`Parameters.numcpu <../Parameters/numcpu>` | Number of Distributed MAPDL processes being used. |  |
| {doc}`Parameters.platform <../Parameters/platform>` | The current platform. |  |
| {doc}`Parameters.real <../Parameters/real>` | Active real constant set |  |
| {doc}`Parameters.revision <../Parameters/revision>` | MAPDL revision version. |  |
| {doc}`Parameters.routine <../Parameters/routine>` | Current routine string as a string. |  |
| {doc}`Parameters.rsys <../Parameters/rsys>` | Active result coordinate system |  |
| {doc}`Parameters.section <../Parameters/section>` | Active section number |  |
| {doc}`Parameters.type <../Parameters/type>` | Active element type |  |
| {doc}`Parameters.units <../Parameters/units>` | Units specified by /UNITS command. |  |

```

````