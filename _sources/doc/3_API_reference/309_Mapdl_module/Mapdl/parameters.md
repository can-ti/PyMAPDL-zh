# parameters

````{property} property Mapdl.parameters

Collection of MAPDL parameters.

Notes
------

See {doc}`Specially named parameters <../1_User_guide/107_设置和检索参数>` for additional notes regarding parameter naming in MAPDL.\
有关 MAPDL 中参数命名的其他说明，请参阅 {doc}`特别命名的参数 <.../1_User_guide/107_设置和检索参数>`。

Examples
--------

Simply list all parameters except for MAPDL MATH parameters.\
只需列出 MAPDL MATH 参数以外的所有参数即可。

```python
>>> mapdl.parameters
ARR                              : ARRAY DIM (3, 1, 1)
PARM_FLOAT                       : 20.0
PARM_INT                         : 10.0
PARM_LONG_STR                    : "stringstringstringstringstringst"
PARM_STR                         : "string"
PORT                             : 50052.0
```

Get a parameter

```python
>>> mapdl.parameters['PARM_FLOAT']
20.0
```

Get an array parameter

```python
>>> mapdl.parameters['ARR']
array([1., 2., 3.])
```



````