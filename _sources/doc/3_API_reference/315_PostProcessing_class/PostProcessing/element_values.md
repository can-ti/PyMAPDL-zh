# element_values

````{method} PostProcessing.element_values(item, comp='', option='AVG')

Compute the element-wise values for a given item and component.\
计算给定 item 和 component 的元素值。

This method uses `Mapdl.etable()` and returns a numpy.ndarray rather than storing it within MAPDL.\
此方法使用 `Mapdl.etable()` 并返回 numpy.ndarray 而不是将其存储在 MAPDL 中。

Parameters:
-----------

  item : *str*
  : Label identifying the item. See the table below in the notes section.\
  请参见注释部分的下表。

  comp : *str* , *`optional`*
  : Component of the item if applicable. See the table below in the notes section.

  option : *str* , *`optional`*
  : Option for storing element table data. One of the following:\
  用于存储单元表数据的选项。以下选项之一：
  - `"MIN"` : Store minimum element nodal value of the specified item component.\
  存储指定项目组件的最小单元节点值。
  - `"MAX"` : Store maximum element nodal value of the specified item component.\
  存储指定项目组件的最大单元节点值。
  - `"AVG"` : Store averaged element centroid value of the specified item component (default).\
  存储指定项目组件的平均单元中心点值（默认值）。

Returns:
--------

  `numpy.ndarray`
  : Numpy array of stresses.

  Return type:
  : `ndarray`

Notes
------

This an incomplete table of element values available to this method. For a full table, see [ETABLE](https://www.mm.bme.hu/~gyebro/files/ans_help_v182/ans_cmd/Hlp_C_ETABLE.html).

```{table}

| Item | Comp | Description | Note |
|---|---|---|---|
| U    | X, Y, Z             | X, Y, or Z structural displacement.  |  |
| ROT  | X, Y, Z             | X, Y, or Z structural rotation.      |  |
| TEMP |                     | Temperature.                         |  |
| PRES |                     | Pressure.                            |  |
| VOLT |                     | Electric potential.                  | 电势 |
| MAG  |                     | Magnetic scalar potential.           | 磁标量势 |
| V    | X, Y, Z             | X, Y, or Z fluid velocity.           | X、Y 或 Z 流体速度 |
| A    | X, Y, Z             | X, Y, or Z magnetic vector potential | X、Y 或 Z 磁矢量势 |
| CONC |                     | Concentration.                       | 浓度 |
| CURR |                     | Current.                             |  |
| EMF  |                     | Electromotive force drop.            |  |
| S    | X, Y, Z, XY, YZ, XZ | Component stress.                    | 应力分量 |
| S    | 1, 2, 3             | Principal stress.                    | 主应力 |
| S    | INT                 | Stress intensity.                    | 应力强度 |
| S    | EQV                 | Equivalent stress.                   | 等效应力 |
| EPEL | X, Y, Z, XY, YZ, XZ | Component elastic strain.            | 弹性应变分量 |
| EPEL | 1, 2, 3             | Principal elastic strain.            | 主弹性应变 |
| EPEL | INT                 | Elastic strain intensity.            | 弹性应变强度 |
| EPEL | EQV                 | Elastic equivalent strain.           | 等效弹性应变 |
| EPTH | X, Y, Z, XY, YZ, XZ | Component thermal strain.            | 热应变分量 |
| EPTH | 1, 2, 3             | Principal thermal strain.            | 主热应变 |
| EPTH | INT                 | Thermal strain intensity.            | 热应变强度 |
| EPTH | EQV                 | Thermal equivalent strain.           | 等效热应变 |
| EPPL | X, Y, Z, XY, YZ, XZ | Component plastic strain.            | 塑性应变分量 |
| EPPL | 1, 2, 3             | Principal plastic strain.            | 主塑性应变 |
| EPPL | INT                 | Plastic strain intensity.            | 塑性应变强度 |
| EPPL | EQV                 | Plastic equivalent strain.           | 等效塑性应变 |
| EPCR | X, Y, Z, XY, YZ, XZ | Component creep strain.              | 蠕变应变分量 |
| EPCR | 1, 2, 3             | Principal creep strain.              | 主蠕变应变 |
| EPCR | INT                 | Creep strain intensity.              | 蠕变应变强度 |
| EPCR | EQV                 | Creep equivalent strain.             | 等效蠕变应变 |


```

Examples
---------

Return the averaged element displacement in the X direction.\
返回 X 方向的平均元素位移。

```python
>>> arr = mapdl.post_processing.element_values("U", "X")
>>> arr
array([1.07396154e-06, 3.15631730e-06, 5.12543515e-06, ...,
       5.41204700e-06, 3.33649806e-06, 1.13836132e-06])
```

Return the maximum element X component stress.\
返回元素 X 方向的最大分量应力。

```python
>>> arr = mapdl.post_processing.element_values("S", "X", "max")
>>> arr
array([-1.12618148, -0.93902147, -0.88121128, ...,  0.        ,
        0.        ,  0.        ])
```

Return the minimum element thermal equivalent strain.

```python
>>> arr = mapdl.post_processing.element_values("EPTH", "EQV", "min")
>>> arr
array([0., 0., 0., ..., 0., 0., 0.])
```




````