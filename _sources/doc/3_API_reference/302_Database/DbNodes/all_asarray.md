# all_asarray

````{method} DbNodes.all_asarray()

Return all node indices, coordinates, and angles as arrays.\
以数组形式返回所有节点索引、坐标和角度。

```{note}
This only returns data of the selected nodes.
```

Returns:
---------

  `np.ndarray`
  : Numpy.int32 array of node numbers with shape (n_node,).

  `np.ndarray`
  : Numpy.double array of node coordinates with shape (n_node, 3).

  `np.ndarray`
  : Numpy.double array of node angles with shape (n_node, 3).

Examples
-----------

Return all the node indices, coordinates, and angles of all the nodes.\
返回所有节点的索引、坐标和角度。

```python
>>> nodes = mapdl.db.nodes
>>> ind, coords, angles = nodes.all_asarray()
>>> ind
array([     1,      2,      3, ..., 270639, 270640, 270641], dtype=int32)

```

```python
>>> coords
array([[0.    , 1.    , 0.    ],
       [0.    , 0.    , 0.    ],
       [0.    , 0.9875, 0.    ],
       ...,
       [0.9875, 0.975 , 0.925 ],
       [0.9875, 0.975 , 0.95  ],
       [0.9875, 0.975 , 0.975 ]])

```

```python
>>> angles
array([[0., 0., 0.],
       [0., 0., 0.],
       [0., 0., 0.],
       ...,
       [0., 0., 0.],
       [0., 0., 0.],
       [0., 0., 0.]])

```

````