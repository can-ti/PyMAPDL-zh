# element_displacement

````{method} PostProcessing.element_displacement(component='ALL', option='AVG')

Return element displacement.

One value per element. Either minimum, maximum, or average of all nodes in each element.\
每个单元一个值。每个单元中所有节点的最小值、最大值或平均值。

Equivalent MAPDL commands:\
等效的 MAPDL 命令：

- `ETABLE,VALUES,U,X`
- `PRETAB,VALUES`
- `*VGET,TMP,ELEM,1,ETAB,VALUES`

Parameters:
--------

  component : *`str`* , *`optional`*
  : Structural displacement component to retrieve. Must be `"X"`, `"Y"`, `"Z"`, `"ALL"` or `"NORM"`. Defaults to `"ALL"`.\
  要检索的结构位移分量。必须是 `"X"`、`"Y"`、`"Z"`、`"ALL"`或 `"NORM"`。默认为 `"ALL"`。

  option : *`str`* , *`optional`*
  : Option for storing element table data. One of the following:\
  用于存储单元表数据的选项。以下选项之一：
  - `"MIN"` : Store minimum element nodal value of the specified item component.\
  存储指定项目组件的最小单元节点值。
  - `"MAX"` : Store maximum element nodal value of the specified item component.\
  存储指定项目组件的最大单元节点值。
  - `"AVG"` : Store averaged element centroid value of the specified item component (default).\
  存储指定项目组件的平均单元中心点值（默认值）。

Returns:
---------

  `numpy.ndarray`
  : Numpy array of displacement.

Examples
----------

Return the average element displacement for all components.\
返回所有元素的平均位移。

```python
>>> arr = mapdl.post_processing.element_displacement("ALL")
>>> arr.shape
(2080, 3)
>>> arr
array([[ 1.07396154e-06, -9.03608033e-06, -5.17768108e-12],
       [ 3.15631730e-06, -2.65527340e-05,  1.07714512e-11],
       [ 5.12543515e-06, -4.31175194e-05,  2.19929719e-12],
       ...,
       [ 5.41204700e-06, -4.80335719e-05,  7.75819589e-11],
       [ 3.33649806e-06, -2.96109417e-05,  1.44947535e-10],
       [ 1.13836132e-06, -1.01038096e-05,  6.95566641e-11]])
```

````