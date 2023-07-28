# DbNodes

````{class} ansys.mapdl.core.database.nodes.DbNodes(db)

Abstract mapdl db nodes class.

Examples
--------

Create a nodes instance.

```python
>>> from ansys.mapdl.core import launch_mapdl
>>> mapdl = launch_mapdl()
>>> # create nodes...
>>> nodes = mapdl.db.nodes
>>>print(nodes)
MAPDL Database Nodes
    Number of nodes:          270641
    Number of selected nodes: 270641
    Maximum node number:      270641
```

```python
>>> mapdl.nsel("NONE")
>>> print(nodes)
MAPDL Database Nodes
    Number of nodes:          270641
    Number of selected nodes: 0
    Maximum node number:      270641
```

Return the selection status and the coordinates of node 22.

```python
>>> nodes = mapdl.db.nodes
>>> sel, coord = nodes.coord(22)
coord
(1.0, 0.5, 0.0, 0.0, 0.0, 0.0)
```

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

Methods
------

```{table}

| | | |
|---|---|--- |
| {doc}`DbNodes.all_asarray() <../DbNodes/all_asarray>` | Return all node indices, coordinates, and angles as arrays. | 以数组形式返回所有节点索引、坐标和角度。|
| {doc}`DbNodes.coord(inod) <../DbNodes/coord>` | Return the location of a node. | 返回节点的位置坐标。 |
| {doc}`DbNodes.first([inod]) <../DbNodes/first>` | Return the number of the first node. | 返回第一个节点的编号。 |
| {doc}`DbNodes.info(inod,ikey) <../DbNodes/info>` | Return information about a node. | 返回一个节点的详细信息。 |
| {doc}`DbNodes.next() <../DbNodes/next>` | Return the number of the next selected node. | 返回下一个选定节点的编号。 |
| {doc}`DbNodes.num([selected]) <../DbNodes/num>` | Return the number of nodes, either selected or all. | 返回所选或全部节点的数量。 |
| {doc}`DbNodes.push(inod,x,y,z[,xang,yang,zang]) <../DbNodes/push>` | Push a single node into the DB.| 将单个节点推入数据库。 |

```

Attributes
-----------

```{table}

| | | |
|---|---|--- |
| {doc}`DbNodes.max_num <../DbNodes/max_num>` | Return the maximum node number. | 返回最大的节点编号。 |

```


````

