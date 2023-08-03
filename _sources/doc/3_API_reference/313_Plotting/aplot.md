# aplot

````{method} Mapdl.aplot(na1='', na2='', ninc='', degen='', scale='', vtk=None, quality=4, show_area_numbering=False, show_line_numbering=False, color_areas=False, show_lines=False, **kwargs)

Display the selected areas.

Displays the selected areas from `na1` to `na2` in steps of `ninc`.

APDL Command: `APLOT`

```{note}
PyMAPDL plotting commands with `vtk=True` ignore any values set with the `PNUM` command.\
使用 `vtk=True` 的 PyMAPDL 绘图命令会忽略使用 `PNUM` 命令设置的任何值。
```

Parameters:
------------

  na1 : *`int`* , *`optional`*
  : Minimum area to display.

  na2 : *`int`* , *`optional`*
  : Maximum area to display.

  ninc : *`int`* , *`optional`*
  : Increment between minimum and maximum area.

  degen : *`str`* , *`optional`*
  : Degeneracy(/dɪ'dʒɛnərəsi/) marker. This option is ignored when `vtk=True`.\
  退化标记。当 `vtk=True` 时，该选项将被忽略。

  scale : *`float`* , *`optional`*
  : Scale factor for the size of the degeneracy-marker star. The scale is the size in window space (-1 to 1 in both directions) (defaults to 0.075). This option is ignored when `vtk=True`.\
  退化标记星大小的比例因子。比例是窗口空间中的大小（双向-1 到 1）（默认为 0.075）。当 `vtk=True` 时，此选项将被忽略。

  vtk : *`bool`* , *`optional`*
  : Plot the currently selected areas using `pyvista`. As this creates a temporary surface mesh, this may have a long execution time for large meshes.\
  使用 `pyvista` 绘制当前选定的区域。由于这会创建一个临时面网格，因此对于大型网格，执行时间可能会较长。

  quality : *`int`* , *`optional`*
  : Quality of the mesh to display. Varies between 1 (worst) to 10 (best) when `vtk=True`.\
  要显示的网格质量。当 `vtk=True` 时，在 1（最差）到 10（最佳）之间变化。

  show_area_numbering : *`bool`* , *`optional`*
  : Display area numbers when `vtk=True`.

  show_line_numbering : *`bool`* , *`optional`*
  : Display line numbers when `vtk=True`.

  color_areas : *`np.array`*, *`optional`*
  : Only used when `vtk=True`. If `color_areas` is a bool, randomly color areas when `True` . If `color_areas` is an array or list, it colors each area with the RGB colors, specified in that array or list.\
  仅在 `vtk=True` 时使用。如果 `color_areas` 为 bool，则在 `True` 时对区域随机着色。如果 `color_areas` 是一个数组或列表，则会使用该数组或列表中指定的 RGB 颜色为每个区域着色。

  show_lines : *`bool`* , *`optional`*
  : Plot lines and areas. Change the thickness of the lines with `line_width=`\
  绘制 lines 和 areas 。用 `line_width=` 改变线条的粗细

  **kwargs
  : See {doc}`ansys.mapdl.core.plotting.general_plotter() <../313_Plotting/general_plotter>` for more keyword arguments applicable when visualizing with `vtk=True`.\
  有关使用 `vtk=True` 进行可视化时适用的更多关键字参数，请参阅 {doc}`ansys.mapdl.core.plotting.general_plotter() <../313_Plotting/general_plotter>`。

Exampels
---------

Plot areas between 1 and 4 in increments of 2.

```python
>>> mapdl.block(0, 1, 0, 1, 0, 1)
>>> mapdl.aplot(1, 4, 2)
```

Plot all areas and randomly color the areas. Label center of areas by their number.\
绘制所有区域，并随机给区域涂上颜色。在区域中心标上编号。

```python
>>> mapdl.aplot(show_area_numbering=True, color_areas=True)
```

Return the plotting instance and modify it.\
返回并修改绘图实例。

```python
>>> mapdl.aplot()
>>> pl = mapdl.aplot(return_plotter=True)
>>> pl.show_bounds()
>>> pl.set_background('black')
>>> pl.add_text('my text')
>>> pl.show()
```


````