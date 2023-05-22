# 访问 MAPDL 数据库
```{warning}
该功能仍处于测试阶段，如果有任何错误或建议，请向 pyansys.support@ansys.com 报告。
```

在 PyMAPDL v0.61.2及更高版本中，您可以使用 DB 模块从 MAPDL 数据库访问单元和节点数据。

## 用法

获取 `elems` 和 `nodes` 对象:

```python
>>> from ansys.mapdl.core import launch_mapdl
>>> from ansys.mapdl.core.examples import vmfiles
>>> mapdl = launch_mapdl()
>>> mapdl.input(vmfiles["vm271"])
>>> elems = mapdl.db.elems
>>> elems
MAPDL Database Elements
   Number of elements:          3459
   Number of selected elements: 3459
   Maximum element number:      3459

>>> nodes = mapdl.db.nodes
MAPDL Database Nodes
   Number of nodes:          3652
   Number of selected nodes: 3652
   Maximum node number:      3652
```

获取第一个单元:
```python
>>> elems = mapdl.db.elems
>>> elems.first()
1
```

检查单元是否被选中:
```python
>>> from ansys.mapdl.core.database import DBDef
>>> elems.info(1, DBDef.DB_SELECTED)
```

返回单元 1 的单元信息:
```python
>>> elems = mapdl.db.elems
>>> elem_info = elems.get(1)
>>> elem_info
ielem: 1
elmdat: 1
elmdat: 1
elmdat: 1
elmdat: 1
elmdat: 0
elmdat: 0
elmdat: 12
elmdat: 0
elmdat: 0
elmdat: 0
nnod: 2
nodes: 1
nodes: 3
```

返回属于单元的节点:
```python
>>> elem_info.nodes
[1, 3]
```

返回单元数据:
```python
>>> elem_info.elmdat
[1, 1, 1, 1, 0, 0, 12, 0, 0, 0]
```

返回选择状态和节点 22 的坐标:
```python
>>> nodes = mapdl.db.nodes
>>> sel, coord = nodes.coord(22)
>>> coord
(-0.0014423144202849985, 0.010955465718673852, 0.0, 0.0, 0.0, 0.0)
```

```{note}
`coord` 方法返回的坐标包含以下内容: X、 Y、 Z、 THXY、 THYZ 和 THZX。
```

## 必要条件
要使用 `DB` 特性(feature)，必须满足以下要求:

- `ansys.api.mapdl` 包版本应该是 0.5.1 或更高版本。
- Ansys MAPDL 版本应该是 2021R1 或更高版本。

```{warning}
这个特性在 Ansys 2023 R1 中不起作用。
```

