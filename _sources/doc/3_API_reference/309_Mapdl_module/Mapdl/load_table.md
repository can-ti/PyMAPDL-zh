# load_table

````{method}

Mapdl.load_table(name, array, var1='', var2='', var3='', csysid='')

Load a table from Python to into MAPDL.

Uses `*tread` to transfer the table.

Parameters:
---------

  name : *`str`*
  : An alphanumeric name used to identify this table. Name may be up to 32 characters, beginning with a letter and containing only letters, numbers, and underscores. Examples: `"ABC" "A3X" "TOP_END"`.\
  用于标识此表的字母数字名称。名称最多可包含 32 个字符，以字母开头，只包含字母、数字和下划线。例如 `"abc" "a3x" "top_end"`。

  array : *`numpy.ndarray`* or *`List`*
  : List as a table or `numpy.ndarray` array.

  var1 : *`str`* , *`optional`*
  : Variable name corresponding to the first dimension (row). Default `"Row"`.\
  与第一个维度（行）相对应的变量名。默认为 `"row"`。\
  A primary variable (listed below) or can be an independent parameter. If specifying an independent parameter, then you must define an additional table for the independent parameter. The additional table must have the same name as the independent parameter and may be a function of one or more primary variables or another independent parameter. All independent parameters must relate to a primary variable.\
  主变量（如下所列），也可以是独立参数。如果指定独立参数，则必须为独立参数定义一个附加表。附加表的名称必须与独立参数相同，并且可以是一个或多个主变量或另一个独立参数的函数。所有独立参数都必须与主变量相关。
  - `"TIME"`: Time
  - `"FREQ"`: Frequency
  - `"X"`: X-coordinate location
  - `"Y"`: Y-coordinate location
  - `"Z"`: Z-coordinate location
  - `"TEMP"`: Temperature
  - `"VELOCITY"`: Velocity
  - `"PRESSURE"`: Pressure
  - `"GAP"`: Geometric gap/penetration 几何间隙/渗透
  - `"SECTOR"`: Cyclic sector number
  - `"OMEGS"`: Amplitude of the rotational velocity vector 旋转速度矢量的振幅
  - `"ECCENT"`: Eccentricity 偏心率
  - `"THETA"`: Phase shift
  - `"ELEM"`: Element number
  - `"NODE"`: Node number
  - `"CONC"`: Concentration

  var2 : *`str`* , *`optional`*
  : Variable name corresponding to the first dimension (column). See var1. Default column.\
  与第一个维度（列）相对应的变量名。请参见 `var1`。默认为 column。

  var3 : *`str`* , *`optional`*
  : Variable name corresponding to the first dimension (plane). See var1. Default plane.\
  与第一个维度（面）相对应的变量名。请参见 `var1`。默认为 plane。

Examples
---------

Transfer a table to MAPDL. The first column is time values and must be ascending in order.\
将表格转入 MAPDL。第一列是时间值，必须按升序排列。

```python
>>> my_conv = np.array([[0, 0.001],
                        [120, 0.001],
                        [130, 0.005],
                        [700, 0.005],
                        [710, 0.002],
                        [1000, 0.002]])
>>> mapdl.load_table('MY_TABLE', my_conv, 'TIME')
>>> mapdl.parameters['MY_TABLE']
array([[0.001],
       [0.001],
       [0.005],
       [0.005],
       [0.002],
       [0.002]])
```


````