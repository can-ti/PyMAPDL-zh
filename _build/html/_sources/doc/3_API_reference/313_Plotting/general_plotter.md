# general_plotter

````{method} ansys.mapdl.core.plotting.general_plotter(meshes, points, labels, *, title='', cpos=None, show_bounds=False, show_axes=True, background=None, off_screen=None, savefig=None, window_size=None, notebook=None, style=None, color='w', show_edges=None, edge_color=None, point_size=5.0, line_width=None, opacity=1.0, flip_scalars=False, lighting=None, n_colors=256, interpolate_before_map=True, cmap=None, render_points_as_spheres=False, render_lines_as_tubes=False, scalar_bar_args={}, smooth_shading=None, show_scalar_bar=None, split_sharp_edges=None, font_size=None, font_family=None, text_color=None, theme=None, return_plotter=False, return_cpos=False, mapdl=None, plot_bc=False, plot_bc_legend=None, plot_bc_labels=None, bc_labels=None, bc_target=None, bc_glyph_size=None, bc_labels_font_size=16, plotter=None, add_points_kwargs={}, add_mesh_kwargs={}, add_point_labels_kwargs={}, plotter_kwargs={})

General pymapdl plotter for APDL geometry and meshes.\
用于 APDL 几何图形和网格的通用 pymapdl 绘图仪。

Parameters:
-----------

  title : *`str`* , *`optional`*
  : Add given title to plot.

  cpos : *`list`(`tuple`(`floats`))* , *`str`*
  : The camera position to use. You can either use a saved camera position or specify one of the following strings:\
  要使用的摄像机位置。您可以使用已保存的摄像机位置或指定以下字符串之一：
  - `"xy"`
  - `"xz"`
  - `"yz"`
  - `"yx"`
  - `"zx"`
  - `"zy"`
  - `"iso"`

  off_screen : *`bool`* , *`optional`*
  : Renders off screen when `True`. Useful for automated screenshots.\
  为 `True` 时在屏幕外渲染。适用于自动截图。

  window_size : *`list`* , *`optional`*
  : Window size in pixels. Defaults to `[1024, 768]`\
  窗口大小（像素）。默认为 `[1024, 768]`

  notebook : *`bool`* , *`optional`*
  : When `True`, the resulting plot is placed inline a jupyter notebook. Assumes a jupyter console is active. Automatically enables `off_screen`.\
  为 `True` 时，生成的绘图将被置于 jupyter notebook 中。假定 jupyter 控制台处于活动状态。自动启用 `off_screen`。

  show_bounds : *`bool`* , *`optional`*
  : Shows mesh bounds when `True`.

  show_axes : *`bool`* , *`optional`*
  : Shows a vtk axes widget. Enabled by default.\
  显示 vtk 坐标轴部件。默认已启用。

  savefig ： *`str`* , *`optional`*
  ： Saves screenshot to a file path.

  style ： *`str`* , *`optional`*
  ： Visualization style of the mesh. One of the following: `style='surface'`, `style='wireframe'`, `style='points'`. Defaults to `'surface'`. Note that `'wireframe'` only shows a wireframe of the outer geometry.\
  网格的可视化样式。以下样式之一：style='surface'`、`style='wireframe'`、`style='point'`。默认为 `'surface'`。请注意，`'wireframe'` 只显示外部几何体的线框。

  color : *`str`* or 3 *`item`* *`list`* , *`optional`*
  : Use to make the entire mesh have a single solid color. Either a string, RGB list, or hex color string. For example: `color='white'`, `color='w'`, `color=[1, 1, 1]`, or `color='#FFFFFF'`. Color will be overridden if scalars are specified.\
  用于使整个网格具有单一的纯色。可以是字符串、RGB 列表或十六进制颜色字符串。例如：`color='white'`、`color='w'`、`color=[1, 1, 1]`或`color='#FFFFFF'`。如果指定标量，颜色将被覆盖。

  show_edges : *`bool`* , *`optional`*
  : Shows the edges of a mesh. Does not apply to a wireframe representation.\
  显示网格的边缘。不适用于线框表示法。

  edge_color : *`str`* or 3 *`item`* *`list`* , *`optional`*
  : The solid color to give the edges when `show_edges=True`. Either a string, RGB list, or hex color string. Defaults to black.\
  当 `show_edges=True` 时边缘的纯色。可以是字符串、RGB 列表或十六进制颜色字符串。默认为黑色。

  point_size : *`float`* , *`optional`*
  : Point size of any nodes in the dataset plotted. Also applicable when `style=’points’`. Default `5.0`.\
绘制的数据集中任何节点的点尺寸。也适用于 `style='points'` 时。默认值 `5.0`.

  line_width : *`float`* , *`optional`*
  : Thickness of lines. Only valid for wireframe and surface representations. Default None.\
  线条的粗细。仅对线框和曲面表示有效。默认为无。

  opacity : *`float`* , *`str`* , *`[array_like](https://numpy.org/doc/stable/glossary.html#term-array_like)`*
  : Opacity(/oʊˈpæsəti/ n.不透明度) of the mesh. If a single float value is given, it will be the global opacity of the mesh and uniformly applied everywhere - should be between 0 and 1. A string can also be specified to map the scalars range to a predefined opacity transfer function (options include: `‘linear’`, `‘linear_r’`, `‘geom’`, `‘geom_r’`). A string could also be used to map a scalars array from the mesh to the opacity (must have same number of elements as the `scalars` argument). Or you can pass a custom made transfer function that is an array either `n_colors` in length or shorter.\
  网格的不透明度。如果给定的是单个浮点数值，那么它将是网格的全局不透明度，并且会均匀地应用到所有地方 - 应该介于 0 和 1 之间。 也可以指定一个字符串，将标量范围映射到预定义的不透明度传递函数（选项包括：`'linear'`、`'linear_r'`、`'geom'`、`'geom_r'`）。也可以使用字符串来映射从网格到不透明度的标量数组（必须与 `scalars` 参数具有相同的元素数）。或者你也可以传递一个自定义的转移函数，它是一个长度为 `n_colors` 或更短的数组。

  n_colors : *`int`* , *`optional`*
  : Number of colors to use when displaying scalars. Defaults to 256. The scalar bar will also have this many colors.\
  显示标量时使用的颜色数。默认为 256。标量栏也会有这么多颜色。

  cmap : *`str`* , *`list`* , *`optional`*
  : Name of the Matplotlib colormap to us when mapping the `scalars`. See available Matplotlib colormaps. Only applicable for when displaying `scalars`. Requires Matplotlib to be installed. `colormap` is also an accepted alias for this. If `colorcet` or `cmocean` are installed, their colormaps can be specified by name.You can also specify a list of colors to override an existing colormap with a custom one. For example, to create a three color colormap you might specify `['green', 'red', 'blue']`.\
  映射 `scalars` 时使用的 Matplotlib colormap 的名称。请参阅可用的 Matplotlib 颜色映射。仅适用于显示 `scalars` 时。需要安装 Matplotlib。`colormap` 也是一个可接受的别名。如果安装了 `colorcet` 或 `cmocean`，则可以通过名称指定它们的颜色图。例如，要创建一个三色颜色表，可以指定 `['green', 'red', 'blue']`。

  render_points_as_spheres : *`bool`* , *`optional`*
  : Render points as spheres.\
  将点渲染为球体。

  render_lines_as_tubes : *`bool`* , *`optional`*
  : Renders lines as tubes.\
  将线条渲染为管状。

  smooth_shading : *`bool`* , *`optional`*
  : Smoothly render curved surfaces when plotting. Not helpful for all meshes.\
  绘图时平滑呈现曲面。并非对所有网格都有帮助。

  theme : *`pyvista.DefaultTheme`*, *`optional`*
  : PyVista theme. Defaults to PyMAPDL theme.

  return_plotter : *`bool`* , *`optional`*
  : Return the plotting object rather than showing the plot and returning the camera position. Default `False`. This overrides the `return_cpos` value.\
  返回绘图对象，而不是显示绘图和返回摄像机位置。默认为 `False`。这将覆盖 `return_cpos` 值。

  return_cpos : *`bool`* , *`optional`*
  : Returns the camera position as an array. Default `False`.\
  以数组形式返回摄像机位置。默认为 `False`。

  mapdl : *`Mapdl instance`* , *`optional`*
  : If you want to use `plot_bc` keyword, the MAPDL instance needs to be passed as argument. Defaults to `None`.\
  如果要使用 `plot_bc` 关键字，则需要将 MAPDL 实例作为参数传递。默认为 "无"。

  plot_bc : *`bool`* , *`optional`*
  : Activate the plotting of the boundary conditions. Defaults to `False`.\
  激活绘制边界条件。默认为 `False`。
  ```{warning}
  This is in alpha state.
  ```

  plot_bc_legend : *`bool`* , *`optional`*
  : Shows the boundary conditions legend. Defaults to `False`.\
  显示边界条件图例。默认为 `False`。

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

  plotter : *`[pyvista.Plotter](https://docs.pyvista.org/version/stable/api/plotting/_autosummary/pyvista.Plotter.html#pyvista.Plotter)`*, *`optional`*
  : If a `pyvista.Plotter` is not provided, then creates its own plotter. If a `pyvista.Plotter` is provided, the plotter is not shown (you need to issue `pyvista.Plotter.show()` manually) and the arguments `notebook`, `off_screen` and `theme` are ignored, since they should be set when instantiated the provided plotter. Defaults to `None` (create the Plotter object).\
  如果没有提供 `pyvista.Plotter`，则会创建自己的绘图仪。如果提供了 `pyvista.Plotter`，则不会显示绘图仪（需要手动发出 `[pyvista.Plotter.show()](https://docs.pyvista.org/version/stable/api/plotting/_autosummary/pyvista.Plotter.show.html#pyvista.Plotter.show)`），并且忽略参数 `notebook`、`off_screen` 和 `theme`，因为它们应该在实例化提供的绘图仪时设置。默认为 `None`（创建绘图仪对象）。

  add_points_kwargs : *`list`[`dict`]*
  : This is a dict or list of dicts to be passed to all or just the correspondent pyvista.Plotter.add_points call in `[ansys.mapdl.core.plotting.general_plotter()](https://mapdl.docs.pyansys.com/version/stable/api/_autosummary/ansys.mapdl.core.plotting.general_plotter.html#ansys.mapdl.core.plotting.general_plotter)`. This pyvista method is used to plot nodes for example. See examples section to learn more about its usage.\
  这是一个 dict 或 dict 列表，将在`[ansys.mapdl.core.plotting.general_plotter()](https://mapdl.docs.pyansys.com/version/stable/api/_autosummary/ansys.mapdl.core.plotting.general_plotter.html#ansys.mapdl.core.plotting.general_plotter)`中传递给所有或仅对应的 pyvista.Plotter.add_points 调用。例如，该 pyvista 方法用于绘制节点。请参阅示例部分了解其更多用法。

  add_mesh_kwargs : `list`[`dict`]
  : This is a dict or list of dicts to be passed to all or just the correspondent `pyvista.Plotter.add_mesh` call in `[ansys.mapdl.core.plotting.general_plotter()](https://mapdl.docs.pyansys.com/version/stable/api/_autosummary/ansys.mapdl.core.plotting.general_plotter.html#ansys.mapdl.core.plotting.general_plotter)`. This pyvista method is used to plot elements for example. See examples section to learn more about its usage.\
  这是一个 dict 或 dict 列表，将传递给 `[ansys.mapdl.core.plotting.general_plotter()](https://mapdl.docs.pyansys.com/version/stable/api/_autosummary/ansys.mapdl.core.plotting.general_plotter.html#ansys.mapdl.core.plotting.general_plotter)`中对应的 `pyvista.Plotter.add_mesh`调用。该 pyvista 方法用于绘制元素图。有关其用法的更多信息，请参阅示例部分。

  add_point_labels_kwargs : `list`[`dict`]
  : This is a dict or list of dicts to be passed to all or just the correspondent `pyvista.Plotter.add_point_labels` call in `[ansys.mapdl.core.plotting.general_plotter()](https://mapdl.docs.pyansys.com/version/stable/api/_autosummary/ansys.mapdl.core.plotting.general_plotter.html#ansys.mapdl.core.plotting.general_plotter)`. This pyvista method is used to plot node labels for example. See examples section to learn more about its usage.\
  这是一个 dict 或 dict 列表，将传递给 `[ansys.mapdl.core.plotting.general_plotter()](https://mapdl.docs.pyansys.com/version/stable/api/_autosummary/ansys.mapdl.core.plotting.general_plotter.html#ansys.mapdl.core.plotting.general_plotter)`中相应的 `pyvista.Plotter.add_point_labels` 调用。例如，该 pyvista 方法用于绘制节点标签。有关其用法的更多信息，请参阅示例部分。

  plotter_kwargs : `dict`
  : This is a dict which is passed to the `pyvista.Plotter` initializer in `[ansys.mapdl.core.plotting.general_plotter()](https://mapdl.docs.pyansys.com/version/stable/api/_autosummary/ansys.mapdl.core.plotting.general_plotter.html#ansys.mapdl.core.plotting.general_plotter)`. This pyvista class is used in all PyMAPDL plots. See examples section to learn more about its usage.

Returns:
-------

  `cpos` or `pyvista.Plotter` or `None`
  : Camera position or instance of `pyvista.Plotter` or None depending on `return_plotter` and `return_cpos`.\
  摄像机位置或 `pyvista.Plotter` 实例或 None（无），取决于 `return_plotter` 和 `return_cpos`。


Notes
--------

Plotting boundary conditions is still under-development, so feel free to share feedback or suggestion in PyMAPDL. At the moment only nodal boundary conditions can be shown (`bc_target='Nodes'`), and only the following types of boundary conditions:\
绘制边界条件仍在开发中，请随时在 PyMAPDL 中分享反馈或建议。目前只能显示节点边界条件 (`bc_target='Nodes'`)，而且只能显示以下类型的边界条件：

```{table}
| Field | Boundary conditions |
| --- | --- |
|MECHANICAL | [“UX”, “UY”, “UZ”, “FX”, “FY”, “FZ”] |
|THERMAL | [“TEMP”, “HEAT”] | 
|ELECTRICAL | [“VOLT”, “CHRGS”, “AMPS”] |
```

Examples
--------

Plot areas and modify the background color to `'black'`\
绘制区域并将背景颜色修改为 `'黑色'`
```python
>>> cpos = mapdl.aplot(background='black')
```

Enable smooth_shading on an element plot.\
在元素图上启用平滑阴影。
```python
>>> cpos = mapdl.eplot(smooth_shading=True)
```

Plot boundary conditions “UX” and “UZ” on the nodes:\
在节点上绘制边界条件 "UX "和 "UZ"：
```python
>>> mapdl.nplot(plot_bc=True, bc_labels=["UX", "UZ"], plot_bc_labels=True)
```

Return the plotting instance, modify it, and display the plot.\
返回绘图实例、修改实例并显示绘图。
```python
>>> pl = mapdl.aplot(return_plotter=True)
>>> pl.show_bounds()
>>> pl.set_background('black')
>>> pl.add_text('my text')
>>> pl.show()
```

Save a screenshot to disk without showing the plot.\
将截图保存到磁盘，但不显示绘图。
```python
>>> mapdl.eplot(background='w', show_edges=True, smooth_shading=True,
                window_size=[1920, 1080], savefig='screenshot.png',
                off_screen=True)
```

Using `add_mesh_kwargs` to pass other arguments to `add_mesh` pyvista method.\
使用 `add_mesh_kwargs` 向 `add_mesh` pyvista 方法传递其他参数。
```python
>>> mapdl.eplot(background='w', show_edges=True, add_mesh_kwargs = {"use_transparency": False})
```

Using `plotter_kwargs` to pass other arguments to `Plotter` constructor.\
使用 `plotter_kwargs` 向 `Plotter` 构造函数传递其他参数。
```python
>>> mapdl.eplot(background='w', show_edges=True, plotter_kwargs = {"polygon_smoothing": False})
```


````