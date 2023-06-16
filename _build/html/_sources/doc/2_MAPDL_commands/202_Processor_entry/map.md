# map

```{py:method} Mapdl.map(kdim='', kout='', limit='', **kwargs)

Maps pressures from source points to target surface elements.\
将压力从源点映射到目标表面单元。

APDL Command: `MAP`

  *kdim*
  : Interpolation key:
    - `"0 or 2"` : Interpolation is done on a surface (default).\
    插值是在一个表面上进行的（默认）。
    - `"3"` : Interpolation is done within a volume. This option is useful if the supplied source data is volumetric field data rather than surface data.\
    插值是在一个体积内进行的。如果提供的源数据是体积场数据而不是表面数据，这个选项很有用。

  *kout*
  : Key to control how pressure is applied when a target node is outside of the source region:\
  控制当目标节点在源区域之外时如何施加压力的关键：
    - `"0"` : Use the pressure(s) of the nearest source point for target nodes outside of the region (default).\对区域外的目标节点使用最近的源点的压力（默认）。
    - `"1"` : Set pressures outside of the region to zero.\
    将区域外的压力设为零。

  *limit*
  : Number of nearby points considered for interpolation. The minimum is 5; the default is 20. Lower values reduce processing time. However, some distorted or irregular meshes will require a higher `LIMIT` value to find the points encompassing the target node in order to define the region for interpolation.\
考虑用于插值的附近点的数量。最小值为5；默认值为20。较低的值可以减少处理时间。然而，一些扭曲或不规则的网格将需要更高的 `LIMIT` 值，以找到包含目标节点的点，从而定义插值的区域。


Notes
---------

Maps pressures from source points to target surface elements.

```