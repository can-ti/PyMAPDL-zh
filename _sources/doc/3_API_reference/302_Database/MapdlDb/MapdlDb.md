# MapdlDb

````{class} ansys.mapdl.core.database.MapdlDb(mapdl)

抽象的 mapdl 数据库类。由 `Mapdl` 实例创建。

Examples
--------

创建一个节点实例。

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

返回节点 22 的选择状态和坐标。

```py

>>> nodes = mapdl.db.nodes
>>> sel, coord = nodes.coord(22)
>>> coord
(1.0, 0.5, 0.0, 0.0, 0.0, 0.0)


```

Methods
----------

```{table}

| | |
|---|---|
| {doc}`MapdlDb.clear(**kwargs) <../MapdlDb/clear>` | 删除 MAPDL 数据库中的所有内容。 |
| {doc}`MapdlDb.load(fname[,progress_bar]) <../MapdlDb/load>` | 在内存中加载 MAPDL 数据库文件。 |
| {doc}`MapdlDb.save(fname[,option]) <../MapdlDb/save>` | 将 MAPDL 数据库保存到磁盘。 |
| {doc}`MapdlDb.start([timeout]) <../MapdlDb/start>` | 启动 gRPC MAPDL 数据库服务器。 |
| {doc}`MapdlDb.stop() <../MapdlDb/stop>` | 关闭 MAPDL 数据库服务并关闭连接。 |

```

Attributes
------------

```{table}

| | |
|---|---|
| {doc}`MapdlDb.active <../MapdlDb/active>` | 返回数据库服务器是否处于活动状态。 |
| {doc}`MapdlDb.elems <../MapdlDb/elems>` | MAPDL 数据库单元接口。 |
| {doc}`MapdlDb.nodes <../MapdlDb/nodes>` | MAPDL 数据库节点接口。 |

```


````