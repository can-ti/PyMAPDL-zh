# areas

````{method} Geometry.areas(quality=4, merge=False)

List of areas from MAPDL represented as `pyvista.PolyData`.

Parameters:
----------

  *quality* : *`int`* , *`optional`*
  : quality of the mesh to display. Varies between 1 (worst) to 10 (best).\
  要显示的网格质量。在 1（最差）到 10（最佳）之间变化。

  *merge* : *`bool`* , *`optional`*
  : Option to merge areas into a single mesh. Default `False` to return a list of areas. When `True`, output will be a single mesh.\
  将 areas 合并为单一网格的选项。默认为 `False`，返回 areas 列表。当 `True` 时，输出将是一个单一的网格。

Returns:
---------

  `list`
  :  List of `pyvista.UnstructuredGrid` meshes representing the active surface areas selected by `ASEL`. If `merge=True`, areas are returned as a single merged UnstructuredGrid.

Examples
-----------

Return a list of areas as indiviudal grids\
以独立网格形式返回 areas 列表

```python
>>> areas = mapdl.areas(quality=3)
>>> areab
[UnstructuredGrid (0x7f14add95040)
  N Cells:      12
  N Points:     20
  X Bounds:     -2.000e+00, 2.000e+00
  Y Bounds:     0.000e+00, 1.974e+00
  Z Bounds:     0.000e+00, 0.000e+00
  N Arrays:     4,
UnstructuredGrid (0x7f14add95ca0)
  N Cells:      12
  N Points:     20
  X Bounds:     -2.000e+00, 2.000e+00
  Y Bounds:     0.000e+00, 1.974e+00
  Z Bounds:     5.500e-01, 5.500e-01
  N Arrays:     4,
...

```

Return a single merged mesh.\
返回合并后的单一网格。

```python
>>> area_mesh = mapdl.areas(quality=3,merge=False)
>>> area_mesh
UnstructuredGrid (0x7f14add95ca0)
  N Cells:      24
  N Points:     30
  X Bounds:     -2.000e+00, 2.000e+00
  Y Bounds:     0.000e+00, 1.974e+00
  Z Bounds:     5.500e-01, 5.500e-01
  N Arrays:     4

```

````