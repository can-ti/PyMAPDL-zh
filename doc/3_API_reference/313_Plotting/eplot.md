# eplot

````{method} Mapdl.eplot(show_node_numbering=False, vtk=None, **kwargs)

Plots the currently selected elements.

APDL Command: `EPLOT`

```{note}
PyMAPDL plotting commands with `vtk=True` ignore any values set with the `PNUM` command.
```

Parameters:
---------

  vtk : *`bool`* , *`optional`*
  : Plot the currently selected elements using `pyvista`. Defaults to current `use_vtk` setting.\
  使用 `pyvista` 绘制当前选中的元素。默认为当前的 `use_vtk` 设置。

  show_node_numbering : *`bool`* , *`optional`*
  : Plot the node numbers of surface nodes.\
  绘制曲面节点的节点编号。

  bc_labels : *`List`[`str`]* , *`Tuple`(`str`)* , *`optional`*
  : List or tuple of strings with the boundary conditions to plot, i.e. `[“UX”, “UZ”]`. You can obtain the allowed boundary conditions by evaluating `ansys.mapdl.core.plotting.BCS`. You can use also the following shortcuts:\
  包含要绘制的边界条件的字符串列表或元组，即 `["UX"、"UZ"]`。您可以通过评估 `ansys.mapdl.core.plotting.BCS`，获得允许的边界条件。您还可以使用以下快捷方式：
  - `‘mechanical’` - To plot the following mechanical boundary conditions: `‘UX’`, `‘UY’`, `‘UZ’`, `‘FX’`, `‘FY’`, and `‘FZ’`. Rotational or momentum boundary conditions are not allowed.\
  `'mechanical'`绘制以下力学边界条件：`'UX'`、`'UY'`、`'UZ'`、`'FX'`、`'FY'` 和 `'FZ'`。不允许使用旋转或动量边界条件。
  - `‘thermal’` - To plot the following boundary conditions: `‘TEMP’` and `‘HEAT’`.\
  `'thermal'` - 绘制以下边界条件：`‘TEMP’` 和 `‘HEAT’`。
  - `‘electrical’` To plot the following electrical boundary conditions: `‘VOLT’`, `‘CHRGS’`, and `‘AMPS’`.\
  `‘electrical’` 绘制以下电气边界条件：`‘VOLT’`、`‘CHRGS’` 和 `‘AMPS’`。

  Defaults to all the allowed boundary conditions present in the responses of `ansys.mapdl.core.Mapdl.dlist()` and `ansys.mapdl.core.Mapdl.flist()`.\
  默认为 `ansys.mapdl.core.Mapdl.dlist()` 和 `ansys.mapdl.core.Mapdl.flist()` 响应中允许的所有边界条件。

  bc_targe : *`List`[`str`]* , *`Tuple`(`str`)* , *`optional`*
  : Specify the boundary conditions target to plot, i.e. “Nodes”, “Elements”. You can obtain the allowed boundary conditions target by evaluating `ansys.mapdl.core.plotting.ALLOWED_TARGETS`. Defaults to only `Nodes`.\
  指定要绘制的边界条件目标，如 "节点"、"元素"。您可以通过评估 `ansys.mapdl.core.plotting.ALLOWED_TARGETS`，获得允许的边界条件目标。默认值仅为 "节点"。

  bc_glyph_size : *`float`* , *`optional`*
  : Specify the size of the glyph used for the boundary conditions plotting. By default is ratio of the bounding box dimensions.\
  指定用于边界条件绘图的字形大小。默认为边界框尺寸的比率。

  bc_labels_font_size : *`float`* , *`optional`*
  : Size of the text on the boundary conditions labels. By default it is 16.\
  边界条件标签上文字的大小。默认为 16。

  **kwargs
  : See `help(ansys.mapdl.core.plotter.general_plotter)` for more keyword arguments related to visualizing using `vtk`.

Examples
----------

```python
>>> mapdl.clear()
>>> mapdl.prep7()
>>> mapdl.block(0, 1, 0, 1, 0, 1)
>>> mapdl.et(1, 186)
>>> mapdl.esize(0.1)
>>> mapdl.vmesh('ALL')
>>> mapdl.vgen(2, 'all')
>>> mapdl.eplot(show_edges=True, smooth_shading=True,
```

Save a screenshot to disk without showing the plot\
将截图保存到磁盘，但不显示绘图

```python
>>> mapdl.eplot(background='w', show_edges=True, smooth_shading=True,
                window_size=[1920, 1080], savefig='screenshot.png',
                off_screen=True)
```


````