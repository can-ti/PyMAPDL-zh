# grid

````{property} property MeshGrpc.grid

VTK representation of the underlying finite element mesh.\
底层有限元网格的 VTK 表示法。

Examples
--------

Store the finite element mesh as a VTK UnstructuredGrid.\
将有限元网格存储为 VTK UnstructuredGrid。

```python
>>> grid = mapdl.mesh.grid
UnstructuredGrid (0x7f99b4135760)
  N Cells:      32198
  N Points:     50686
  X Bounds:     -1.181e+00, 1.181e+00
  Y Bounds:     -2.362e-01, 0.000e+00
  Z Bounds:     -2.394e+00, 2.509e+00
  N Arrays:     10
```

Plot this grid.

```python
>>> grid.plot() 
```

Access the node numbers of grid.\
访问网格的节点编号。

```python
>>> grid.point_data
Contains keys:
    ansys_node_num
    vtkOriginalPointIds
    origid
    VTKorigID
```

```python
>>> grid.point_data['ansys_node_num']
pyvista_ndarray([    1,     2,     3, ..., 50684, 50685, 50686],
                dtype=int32)
```

Save this grid to disk

```python
grid.save('grid.vtk')
```

Load this grid externally with ParaView or with pyvista\
使用 ParaView 或 pyvista 从外部加载该网格

```python
>>> import pyvista
>>> pyvista.read('grid.vtk')
```


````