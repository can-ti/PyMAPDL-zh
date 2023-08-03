# math

````{property} property MapdlGrpc.math

APDL math interface

Returns:
---------

  `MapdlMath`
  : 

Examples
--------

Get the stiffness matrix from MAPDL\
从 MAPDL 获取刚度矩阵


```python
>>> mm = mapdl.math.stiff()
>>> matrix = k.asarray()
<60x60 sparse matrix of type '<class 'numpy.float64'>'
    with 1734 stored elements in Compressed Sparse Row format>
```

Get the mass matrix from mapdl

```python
>>> mm = mapdl.math.stiff()
>>> matrix = k.asarray()
<60x60 sparse matrix of type '<class 'numpy.float64'>'
    with 1734 stored elements in Compressed Sparse Row format>
```


````