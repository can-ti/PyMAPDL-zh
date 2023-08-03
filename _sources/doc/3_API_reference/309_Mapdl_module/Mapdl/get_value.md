# get_value

````{method} Mapdl.get_value(entity='', entnum='', item1='', it1num='', item2='', it2num='', item3='', it3num='', item4='', it4num='', **kwargs)

Runs the MAPDL GET command and returns a Python value.\
运行 MAPDL GET 命令并返回 Python 值。

This method uses {doc}`Mapdl.get() <../Mapdl/get>`.

See the full MADPL command documentation at [*GET](https://www.mm.bme.hu/~gyebro/files/ans_help_v182/ans_cmd/Hlp_C_GET.html)

```{note}
This method is not available when within the Mapdl.non_interactive() context manager.\
在 Mapdl.non_interactive() 上下文管理器中，此方法不可用。
```

Parameters:
----------

*entity* : *`str`*
  Entity keyword. Valid keywords are `'NODE'`, `'ELEM'`, `'KP'`, `'LINE'`, `'AREA'`, `'VOLU'`, `'PDS'`, etc.\
  实体关键字。有效的关键字有`'NODE'`、`'ELEM'`、`'KP'`、`'LINE'`、`'AREA'`、`'VOLU'`、`'PDS'`等。。

  *entnum* : *`str`* , *`int`* , *`optional`*
  : The number or label for the entity. In some cases, a zero (or blank `''`) *ENTNUM* represents all entities of the set.\
  实体的编号或标签。在某些情况下，零（或空白 `'''`）*ENTNUM* 表示集合中的所有实体。。

  *item1* : *`str`* , *`optional`*
  : The name of a particular item for the given entity. \
  给定实体的特定项目名称。

  *it1num* : *`str`* , *`int`* , *`optional`*
  : The number (or label) for the specified *Item1* (if any).Some *Item1* labels do not require an *IT1NUM* value.\
  指定 *Item1*（如果有）的编号（或标签）。某些 *Item1* 标签不需要 *IT1NUM* 值。

  *item2, it2num*
  : A second set of item labels and numbers to further qualify the item for which data are to be retrieved. Most items do not require this level of information.\
  第二组项目标签和编号，用于进一步限定要检索数据的项目。大多数项目不需要这一级别的信息。

Returns:
----------

  *`float`*
  : Floating point value of the parameters.

Examples:
----------

Retrieve the number of nodes.

```python
>>> value = ansys.get_value('node', '', 'count')
>>> value
3003
```

Retrieve the number of nodes using keywords.

```python
>>> value = ansys.get_value(entity='node', item1='count')
>>> value
3003
```

````