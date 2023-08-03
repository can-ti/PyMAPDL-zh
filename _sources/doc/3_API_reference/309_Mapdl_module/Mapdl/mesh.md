# mesh

````{property} property Mapdl.mesh

Mesh information.

Returns:
--------

  `Mapdl.Mesh`
  : 


Examples
----------

Return an array of the active nodes

```python
>>> mapdl.mesh.nodes
array([[ 1.,  0.,  0.],
       [ 2.,  0.,  0.],
       [ 3.,  0.,  0.],
       [ 4.,  0.,  0.],
       [ 5.,  0.,  0.],
       [ 6.,  0.,  0.],
       [ 7.,  0.,  0.],
       [ 8.,  0.,  0.],
       [ 9.,  0.,  0.],
       [10.,  0.,  0.]])
```

Return an array of the node numbers of the active nodes

```python
>>> mapdl.mesh.nnum
array([ 1,  2,  3,  4,  5,  6,  7,  8,  9, 10], dtype=int32)
```

Simply query and print the geometry

```python
>>> print(mapdl.mesh)
  ANSYS Mapdl Mesh
  Number of Nodes:              321
  Number of Elements:           40
  Number of Element Types:      1
  Number of Node Components:    2
  Number of Element Components: 2
```

Access the geometry as a VTK object\
以 VTK 对象的形式访问几何体

```python
>>> mapdl.mesh.grid
```



````