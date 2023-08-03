# element_stress

````{method} PostProcessing.element_stress(component, option='AVG')

Return element component or principal stress.

One value per element. Either minimum, maximum, or average of all nodes in each element.\
每个元素一个值。每个元素中所有节点的最小值、最大值或平均值。

Equivalent MAPDL commands:

- `ETABLE,VALUES,S,X`
- `PRETAB,VALUES`
- `*VGET,TMP,ELEM,1,ETAB,VALUES`

Parameters:
----------

  component : *`str`*
  : Element stress to retrieve. One of the following:\要检索的元素应力。以下选项之一
  ```{table}
  | | |
  |---|---|
  | X, Y, Z, XY, YZ, XZ | Component stress. |
  | 1, 2, 3 | Principal stress. |
  | INT | Stress intensity. |
  | EQV | Equivalent stress |
  ```

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
  : Numpy array of stresses.

Examples
----------

Return the average element component stress in the X direction.\
返回 X 方向的平均元素应力分量。

```python
>>> arr = mapdl.post_processing.element_stress("X")
>>> arr.shape
(2080, 3)
>>> arr
array([-0.29351357, -0.37027832, -0.37340827, ...,  0.        ,
        0.        ,  0.        ])
```



````