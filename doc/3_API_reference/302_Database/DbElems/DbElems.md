# DbElems

````{class} ansys.mapdl.core.database.elems.DbElems(db)

Abstract mapdl database element class.\
抽象的 mapdl 数据库元素类。

Example
-----------

Create a MAPDL database element instance.

```python
>>> from ansys.mapdl.core import launch_mapdl
>>> mapdl = launch_mapdl()
>>> elems = mapdl.db.elems
>>> print(elems)
MAPDL Database Elements
    Number of elements:          64
    Number of selected elements: 64
    Maximum element number:      64
```

Return the element information of element 1.

```python
>>> elems = mapdl.db.elems
>>> elem_info = elems.get(1)
```

Return the nodes belonging to the element.

```python
>>> elem_info.nodes
[2, 27, 37, 8]
```

Return the element data.

```python
>>> elem_info.elmdat
[1, 1, 1, 1, 0, 0, 14, 0, 0, 0]
```

Methods
---------

```{table}

| | |
|---|---|
| {doc}`DbElems.first([ielm]) <../DbElems/first>` | 获取第一个单元的编号。 |
| {doc}`DbElems.get(ielm) <../DbElems/get>` | 获取单元的属性和节点。 |
| {doc}`DbElems.info(ielm,ikey) <../DbElems/info>` | 获取单元信息。 |
| {doc}`DbElems.next() <../DbElems/next>` | 返回下一个选定单元的编号。 |
| {doc}`DbElems.num([selected]) <../DbElems/num>` | 单元数量。 |
| {doc}`DbElems.push(ielm,elmdat,nodes) <../DbElems/push>` | 将单元放入数据库。|

```

Attributes
-----------

```{table}

| | |
|---|---|
| {doc}`DbElems.max_num <../DbElems/max_num>` | 最大单元编号。 |

```



````