# Geometry


````{class} ansys.mapdl.core.mapdl_geometry.Geometry(mapdl)

Pythonic representation of MAPDL CAD geometry.

Contains advanced methods to extend geometry building and selection within MAPDL.\
包含扩展 MAPDL 中几何体构建和选择的高级方法。

Methods
---------

```{table}
| | | |
|---|---|---|
| {doc}`Geometry.area_select(items[, sel_type, ...]) <../Geometry/area_select>` | Select areas using a sequence of items. | 使用项目序列选择区域。 |
| {doc}`Geometry.areas([quality,merge])  <../Geometry/areas>` | List of areas from MAPDL represented as pyvista.PolyData. | 以 pyvista.PolyData 表示的 MAPDL areas 列表。 |
| {doc}`Geometry.generate_surface([density,amin,...])  <../Geometry/generate_surface>` | Generate an all-triangular surface of the active surfaces. | 生成所选择曲面的全三角形曲面。 |
| {doc}`Geometry.keypoint_select(items[,sel_type,...])  <../Geometry/keypoint_select>` | Select keypoints using a sequence of items. | 使用项目序列选择关键点。 |
| {doc}`Geometry.line_select(items[, sel_type, ...])  <../Geometry/line_select>` | Select lines using a sequence of items. | 使用项目序列选择线条。 |
| {doc}`Geometry.volume_select(items[, sel_type, ...])  <../Geometry/volume_select>` | Select volumes using a sequence of items. | 使用项目序列选择体。 |
```

Attributes
-----------

```{table}
| | |
|---|---|
| {doc}`Geometry.anum <../Geometry/anum>` | Array of area numbers. |
| {doc}`Geometry.keypoints <../Geometry/keypoints>` | Keypoint coordinates |
| {doc}`Geometry.knum <../Geometry/knum>` | Array of keypoint numbers. |
| {doc}`Geometry.lines <../Geometry/lines>` | Active lines as a pyvista.PolyData |
| {doc}`Geometry.lnum <../Geometry/lnum>` | Array of line numbers. |
| {doc}`Geometry.n_area <../Geometry/n_area>` | Number of areas currently selected. |
| {doc}`Geometry.n_keypoint <../Geometry/n_keypoint>` | Number of keypoints currently selected. |
| {doc}`Geometry.n_line <../Geometry/n_line>` | Number of lines currently selected. |
| {doc}`Geometry.n_volu <../Geometry/n_volu>` | Number of volumes currently selected |
| {doc}`Geometry.vnum <../Geometry/vnum>` | Array of volume numbers. |
```

````
