# nodes

````{py:property} property MapdlDb.nodes

MAPDL database nodes interface.

Returns:
-------

`**DbNodes**`

Examples
----------

Create a nodes instance.

```py
>>> from ansys.mapdl.core import launch_mapdl
>>> mapdl = launch_mapdl()
>>> # create nodes...
>>> nodes = mapdl.db.nodes
>>> print(nodes)
MAPDL Database Nodes
    Number of nodes:          270641
    Number of selected nodes: 270641
    Maximum node number:      270641
```

```py
>>> mapdl.nsel("NONE")
>>> print(nodes)
MAPDL Database Nodes
    Number of nodes:          270641
    Number of selected nodes: 0
    Maximum node number:      270641
```

Return the selection status and the coordinates of node 22.

```py
>>> nodes = mapdl.db.nodes
>>> sel, coord = nodes.coord(22)
coord
(1.0, 0.5, 0.0, 0.0, 0.0, 0.0)
```

Return all the node indices, coordinates, and angles of all the nodes.

```py
>>> nodes = mapdl.db.nodes
>>> ind, coords, angles = nodes.all_asarray()
>>> ind
array([     1,      2,      3, ..., 270639, 270640, 270641], dtype=int32)
```

```py
>>> coords
array([[0.    , 1.    , 0.    ],
       [0.    , 0.    , 0.    ],
       [0.    , 0.9875, 0.    ],
       ...,
       [0.9875, 0.975 , 0.925 ],
       [0.9875, 0.975 , 0.95  ],
       [0.9875, 0.975 , 0.975 ]])
```

```py
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