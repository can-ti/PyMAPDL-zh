# element_temperature

````{method} PostProcessing.element_temperature(option='AVG')

Return element temperature.

One value per element. Either minimum, maximum, or average of all nodes in each element.

Equilvanent MAPDL commands:

- `ETABLE,VALUES,TEMP`
- `PRETAB,VALUES`
- `*VGET,TMP,ELEM,1,ETAB,VALUES`

Parameters:
----------

  option : *`str`* , *`optional`*
  : Option for storing element table data. One of the following:\
  用于存储单元表数据的选项。以下选项之一：
  - `"MIN"` : Store minimum element nodal value of the specified item component.\
  存储指定项目组件的最小单元节点值。
  - `"MAX"` : Store maximum element nodal value of the specified item component.\
  存储指定项目组件的最大单元节点值。
  - `"AVG"` : Store averaged element centroid value of the specified item component (default).\
  存储指定项目组件的平均单元中心点值（默认值）。

Examples
----------

Return the average element temperature.

```python
>>> arr = mapdl.post_processing.element_temperature()
>>> arr.shape
(2080, 3)
>>> arr
array([20., 20., 20., ..., 20., 20., 20.])
```



````