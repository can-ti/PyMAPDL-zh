# Inline functions 

These are wrapped versions of inline APDL functions that perform operations like finding the x-coordinate of a node given its number (`Query.nx`).\
这些是“内联 APDL 函数”的封装版本，用于执行给定节点编号（`Query.nx`）后查找节点 x 坐标等操作。

````{class} ansys.mapdl.core.inline_functions.Query(mapdl)

Class containing all the inline functions of APDL.\
包含 APDL 所有内联函数的类。

Most of the results of these methods are shortcuts for specific combinations of arguments supplied to `ansys.mapdl.core.Mapdl.get().`\
这些方法的大多数结果都是提供给 `ansys.mapdl.core.Mapdl.get()` 的特定参数组合的快捷方式。

Currently implemented functions:\
目前已实现的函数：

- `centrx(e)` - get the centroid x-coordinate of element e
- `centry(e)` - get the centroid y-coordinate of element e
- `centrz(e)` - get the centroid z-coordinate of element e
- `nx(n)` - get the x-coordinate of node n
- `ny(n)` - get the y-coordinate of node n
- `nz(n)` - get the z-coordinate of node n
- `kx(k)` - get the x-coordinate of keypoint k
- `ky(k)` - get the y-coordinate of keypoint k
- `kz(k)` - get the z-coordinate of keypoint k
- `lx(n, lfrac)` - X-coordinate of line n at length fraction lfrac
- `ly(n, lfrac)` - Y-coordinate of line n at length fraction lfrac
- `lz(n, lfrac)` - Z-coordinate of line n at length fraction lfrac
- `lsx(n, lfrac)` - X-slope of line n at length fraction lfrac
- `lsy(n, lfrac)` - Y-slope of line n at length fraction lfrac
- `lsz(n, lfrac)` - Z-slope of line n at length fraction lfrac
- `ux(n)` - get the structural displacement at node n in x
- `uy(n)` - get the structural displacement at node n in y
- `uz(n)` - get the structural displacement at node n in z
- `rotx(n)` - get the rotational displacement at node n in x
- `roty(n)` - get the rotational displacement at node n in y
- `rotz(n)` - get the rotational displacement at node n in z
- `nsel(n)` - get the selection status of node n
- `ksel(k)` - get the selection status of keypoint k
- `lsel(n)` - get the selection status of line n
- `asel(a)` - get the selection status of area a
- `esel(n)` - get the selection status of element e
- `vsel(v)` - get the selection status of volume v
- `ndnext(n)` - get the next selected node with a number greater than n.
- `kpnext(k)` - get the next selected keypoint with a number greater than k.
- `lsnext(n)` - get the next selected line with a number greater than n.
- `arnext(a)` - get the next selected area with a number greater than a.
- `elnext(e)` - get the next selected element with a number greater than e.
- `vlnext(v)` - get the next selected volume with a number greater than v.
- `nnear(n)` - get the selected node nearest node n.
- `knear(k)` - get the selected keypoint nearest keypoint k.
- `enearn(n)` - get the selected element nearest node n.
- `node(x, y, z)` - get the node closest to coordinate (x, y, z)
- `kp(x, y, z)` - get the keypoint closest to coordinate (x, y, z)

Examples
---------

In this example we construct a solid box and mesh it. Then we use the `Query` methods `nx`, `ny`, and `nz` to find the cartesian coordinates of the first node. We can access these through the `mapdl.queries` property.\
在本例中，我们构建了一个实心立方体并将其网格化。然后，我们使用 `Query`（查询）方法 `nx`、`ny` 和 `nz` 查找第一个节点的笛卡尔坐标。我们可以通过 `mapdl.queries` 属性访问这些方法。

```python
>>> from ansys.mapdl.core import launch_mapdl
>>> mapdl = launch_mapdl()
>>> mapdl.prep7()
>>> mapdl.et(1, 'SOLID5')
>>> mapdl.block(0, 10, 0, 20, 0, 30)
>>> mapdl.esize(2)
>>> mapdl.vmesh('ALL')
>>> q = mapdl.queries
>>> q.nx(1), q.ny(1), q.nz(1)
0.0 20.0 0.0
```

```{table}

| | | |
|---|---|---|
| {doc}`Query.node(x, y, z) <../305_Inline_functions/node>` | Return node closest to coordinate (x, y, z). |
| {doc}`Query.kp(x, y, z) <../305_Inline_functions/kp>` | Return keypoint closest to coordinate (x, y, z). |
| {doc}`Query.centrx(e) <../305_Inline_functions/centrx>` | Return the x coordinate of the element centroid. |
| {doc}`Query.centry(e) <../305_Inline_functions/centry>` | Return the y coordinate of the element centroid. |
| {doc}`Query.centrz(e) <../305_Inline_functions/centrz>` | Return the z coordinate of the element centroid. |
| {doc}`Query.kx(k) <../305_Inline_functions/kx>` | Return the x coordinate of a keypont. |
| {doc}`Query.ky(k) <../305_Inline_functions/ky>` | Return the y coordinate of a keypont. |
| {doc}`Query.kz(k) <../305_Inline_functions/kz>` | Return the z coordinate of a keypont. |
| {doc}`Query.nx(n) <../305_Inline_functions/nx>` | Return the x coordinate of a node. |
| {doc}`Query.ny(n) <../305_Inline_functions/ny>` | Return the y coordinate of a node. |
| {doc}`Query.nz(n) <../305_Inline_functions/nz>` | Return the z coordinate of a node. |
| {doc}`Query.ux(n) <../305_Inline_functions/ux>` | Returns x-component of structural displacement at a node. |
| {doc}`Query.uy(n) <../305_Inline_functions/uy>` | Returns y-component of structural displacement at a node. |
| {doc}`Query.uz(n) <../305_Inline_functions/uz>` | Returns z-component of structural displacement at a node. |
| {doc}`Query.rotx(n) <../305_Inline_functions/rotx>` | Returns x-component of rotational displacement at a node. |
| {doc}`Query.roty(n) <../305_Inline_functions/roty>` | Returns y-component of rotational displacement at a node. |
| {doc}`Query.rotz(n) <../305_Inline_functions/rotz>` | Returns z-component of rotational displacement at a node. |
| {doc}`Query.lx(n, lfrac) <../305_Inline_functions/lx>` | X-coordinate of line `n` at length fraction `lfrac`. |
| {doc}`Query.ly(n, lfrac) <../305_Inline_functions/ly>` | Y-coordinate of line `n` at length fraction `lfrac`. |
| {doc}`Query.lz(n, lfrac) <../305_Inline_functions/lz>` | Z-coordinate of line `n` at length fraction `lfrac`. |
| {doc}`Query.lsx(n, lfrac) <../305_Inline_functions/lsx>` | X-slope of line `n` at length fraction `lfrac`. |
| {doc}`Query.lsy(n, lfrac) <../305_Inline_functions/lsy>` | Y-slope of line `n` at length fraction `lfrac`. |
| {doc}`Query.lsz(n, lfrac) <../305_Inline_functions/lsz>` | Z-slope of line `n` at length fraction `lfrac`. |
| {doc}`Query.nsel(n) <../305_Inline_functions/nsel>` | Returns selection status of a node. |
| {doc}`Query.ksel(k) <../305_Inline_functions/ksel>` | Returns selection status of a keypoint. |
| {doc}`Query.lsel(n) <../305_Inline_functions/lsel>` | Returns selection status of a line. |
| {doc}`Query.asel(a) <../305_Inline_functions/ksel>` | Returns selection status of an area. |
| {doc}`Query.esel(e) <../305_Inline_functions/esel>` | Returns selection status of an element. |
| {doc}`Query.vsel(v) <../305_Inline_functions/vsel>` | Returns selection status of a volume. |


```

````