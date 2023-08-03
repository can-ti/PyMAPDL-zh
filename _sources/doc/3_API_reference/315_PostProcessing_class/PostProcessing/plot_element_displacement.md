# plot_element_displacement

````{method} PostProcessing.plot_element_displacement(component='NORM', option='AVG', show_elem_numbering=False, **kwargs)

Plot element displacement.

Parameters:
-----------

  component : *`str`* , *`optional`*
  : Structural displacement component to retrieve. Must be `"X"`, `"Y"`, `"Z"`, `"ALL"` or `"NORM"`.\
  要检索的结构位移分量。必须是 `"X"`、`"Y"`、`"Z"`、`"ALL"`或 `"NORM"`。

  option : *`str`* , *`optional`*
  : Option for storing element table data. One of the following:\
  用于存储单元表数据的选项。以下选项之一：
  - `"MIN"` : Store minimum element nodal value of the specified item component.\
  存储指定项目组件的最小单元节点值。
  - `"MAX"` : Store maximum element nodal value of the specified item component.\
  存储指定项目组件的最大单元节点值。
  - `"AVG"` : Store averaged element centroid value of the specified item component (default).\
  存储指定项目组件的平均单元中心点值（默认值）。

  show_elem_numbering: *`bool`* , *`optional`*
  : Plot the element numbers of the elements.

  **kwargs : *`dict`*, *`optional`*
  : Keyword arguments passed to `general_plotter`.

Returns:
----------

  `[pyvista.plotting.renderer.CameraPosition](https://docs.pyvista.org/version/stable/api/plotting/_autosummary/pyvista.CameraPosition.html#pyvista.CameraPosition)`
  : Camera position from plotter. Can be reused as an input parameter to use the same camera position for future plots. Only returned when `return_cpos` is `True`.\
  来自绘图仪的相机位置。可作为输入参数重复使用，以便在以后的绘图中使用相同的相机位置。只有当 `return_cpos` 为 `True`时才会返回。

Notes
-----

If `vkt=True` (default), this function uses `general_plotter` You can pass key arguments to `general_plotter` using `kwargs` argument. For example, `show_axes` , `background`, etc.\
如果 `vkt=True`（默认），该函数将使用 `general_plotter` 您可以使用 `kwargs` 参数将关键参数传递给 `general_plotter` 。例如，`show_axes`、`background` 等。

Examples
---------

Plot the mean normalized element displacement for the first result in the “X” direction.\
绘制第一个结果在 "X" 方向上的平均元素位移。

```python
>>> mapdl.post1()
>>> mapdl.set(1, 1)
>>> mapdl.post_processing.plot_element_displacement(
    "NORM",
    option="AVG"
)
```

````