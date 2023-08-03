# vplot

````{method} Mapdl.vplot(nv1='', nv2='', ninc='', degen='', scale='', vtk=None, quality=4, show_area_numbering=False, show_line_numbering=False, color_areas=False, show_lines=True, **kwargs)

Plot the selected volumes.

APDL Command: `VPLOT`

```{note}
PyMAPDL plotting commands with vtk=True ignore any values set with the PNUM command.
```

Parameters:
----------

  nv1, nv2, ninc
  : Display volumes from NV1 to NV2 (defaults to NV1) in steps of NINC (defaults to 1). If NV1 = ALL (default), NV2 and NINC are ignored and all selected volumes [VSEL] are displayed. Ignored when `vtk=True`.\
  以 NINC（默认为 1）为步长显示从 NV1 到 NV2（默认为 NV1）的加密卷。如果 NV1 = ALL（默认），则忽略 NV2 和 NINC，显示所有选定的卷 [VSEL]。当 `vtk=True` 时忽略。

  degen
  : Degeneracy marker. `"blank"` No degeneracy marker is used (default), or `"DEGE"`. A red star is placed on keypoints at degeneracies (see the Modeling and Meshing Guide). Not available if /FACET,WIRE is set. Ignored when `vtk=True`.\
  退化标记。不使用退化标记（默认），或 `"DEGE"。在退化处的关键点上会有一颗红星（请参阅《建模与网格划分指南》）。如果设置了 /FACET,WIRE，则不可用。当 `vtk=True` 时忽略。

  scale
  : Scale factor for the size of the degeneracy-marker star. The scale is the size in window space (-1 to 1 in both directions) (defaults to .075). Ignored when `vtk=True`.\
  退化标记星大小的比例因子。缩放因子是窗口空间中的大小（双向-1 到 1）（默认为 0.075）。当 `vtk=True` 时忽略。

  vtk : *`bool`* , *`optional`*
  : Plot the currently selected volumes using `pyvista`. As this creates a temporary surface mesh, this may have a long execution time for large meshes.\
  使用 `pyvista` 绘制当前选定的体积。由于这会创建一个临时曲面网格，因此对于大型网格，执行时间可能会较长。

  quality : *`int`* , *`optional`*
  : quality of the mesh to display. Varies between 1 (worst) to 10 (best). Applicable when `vtk=True`.

  show_numbering : *`bool`* , *`optional`*
  : Display line and keypoint numbers when `vtk=True`.

  **kwargs
  : See {doc}`ansys.mapdl.core.plotting.general_plotter() <../313_Plotting/general_plotter>` for more keyword arguments applicable when visualizing with `vtk=True`.

Examples
----------

Plot while displaying area numbers.

```python
>>> mapdl.vplot(show_area_numbering=True)
```

````