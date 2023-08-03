# nplot

````{method} Mapdl.nplot(nnum='', vtk=None, **kwargs)

APDL Command: `NPLOT`

Displays nodes.

```{note}
PyMAPDL plotting commands with `vtk=True` ignore any values set with the `PNUM` command.\
使用 `vtk=True` 的 PyMAPDL 绘图命令会忽略使用 `PNUM` 命令设置的任何值。
```

Parameters:
-----------

  nnum : *`bool`* , *`int`* , *`optional`*
  : Node number key:
  - `False` :  No node numbers on display (default).
  - `True` : Include node numbers on display.

  ```{note}
  This parameter is only valid when `vtk==True`
  ```

  vtk : *`bool`* , *`optional`*
  : Plot the currently selected nodes using `pyvista`. Defaults to current `use_vtk` setting as set on the initialization of MAPDL.\
  使用 `pyvista` 绘制当前选中的节点。默认使用 MAPDL 初始化时设置的当前 `use_vtk` 设置。

  plot_bc : *`bool`* , *`optional`*
  : Activate the plotting of the boundary conditions. Defaults to `False`.\
  激活绘制边界条件。默认为 `False`。
  
  ```{warning}
  This is in alpha state.
  ```

  plot_bc_legend : *`bool`* , *`optional`*
  : Shows the boundary conditions legend. Defaults to `False`\
  显示边界条件图例。默认为 `False`

  plot_bc_labels : *`bool`* , *`optional`*
  : Shows the boundary conditions label per node. Defaults to `False`.\
  显示每个节点的边界条件标签。默认为 `False`。

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

Examples
----------

Plot using VTK while showing labels and changing the background.\
使用 VTK 绘图，同时显示标签和更改背景。

```python
>>> mapdl.prep7()
>>> mapdl.n(1, 0, 0, 0)
>>> mapdl.n(11, 10, 0, 0)
>>> mapdl.fill(1, 11, 9)
>>> mapdl.nplot(
    nnum=True,
    vtk=True,
    background='w',
    color='k',
    show_bounds=True
)
```

Plot without using VTK.

```python
>>> mapdl.prep7()
>>> mapdl.n(1, 0, 0, 0)
>>> mapdl.n(11, 10, 0, 0)
>>> mapdl.fill(1, 11, 9)
>>> mapdl.nplot(vtk=False)
```

Plot nodal boundary conditions.

```python
>>> mapdl.nplot(
    plot_bc=True,
    plot_bc_labels=True,
    bc_labels="mechanical",
)
```




````