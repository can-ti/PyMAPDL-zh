# get

````{method} Mapdl.get(par='__floatparameter__', entity='', entnum='', item1='', it1num='', item2='', it2num='', item3='', it3num='', item4='', it4num='', **kwargs)

Retrieves a value and stores it as a scalar parameter or part of an array parameter.\
读取数值并将其存储为标量参数或数组参数的一部分。

APDL Command: `*GET`

See the full MADPL command at [*GET](https://www.mm.bme.hu/~gyebro/files/ans_help_v182/ans_cmd/Hlp_C_GET.html)

Parameters:
----------

  *par* : *`str`* , *`optional`*
  : The name of the resulting parameter. See *SET for name restrictions.\
  结果参数的名称。有关名称限制，请参阅 *SET。

  *entity* 
  Entity keyword. Valid keywords are NODE, ELEM, KP, LINE, AREA, VOLU, PDS, etc., as shown for Entity = in the tables below.\
  Entity 关键字。有效的关键字有 NODE、ELEM、KP、LINE、AREA、VOLU、PDS 等，如下表中 *Entity*= 所示。

  *entnum*
  : The number or label for the entity (as shown for *ENTNUM* = in the tables below). In some cases, a zero (or blank) *ENTNUM* represents all entities of the set.\
  实体的编号或标签（如下表中 ENTNUM = 所示）。在某些情况下，零（或空白）的 ENTNUM 表示集合中的所有实体。

  *item1*
  : The name of a particular item for the given entity. Valid items are as shown in the *Item1* columns of the tables below.\
  给定实体的特定项目名称。有效项目如下表中 *Item1* 列所示。

  *it1num*
  : The number (or label) for the specified *Item1* (if any). Valid *IT1NUM* values are as shown in the *IT1NUM* columns of the tables below. Some *Item1* labels do not require an *IT1NUM* value.\
  指定 *Item1*（如果有）的编号（或标签）。有效的 *IT1NUM* 值如下表中的 *IT1NUM* 列所示。某些 *Item1* 标签不需要 *IT1NUM* 值。

  *item2, it2num*
  : A second set of item labels and numbers to further qualify the item for which data are to be retrieved. Most items do not require this level of information.\
  第二组项目标签和编号，用于进一步限定要检索数据的项目。大多数项目不需要这一级别的信息。


Notes
--------

*GET retrieves a value for a specified item and stores the value as a scalar parameter, or as a value in a user-named array parameter. An item is identified by various keyword, label, and number combinations. Usage is similar to the *SET command except that the parameter values are retrieved from previously input or calculated results. For example, *GET,A,ELEM,5,CENT,X returns the centroid x-location of element 5 and stores the result as parameter A. *GET command operations, along with the associated Get functions return values in the active coordinate system unless stated otherwise. A Get function is an alternative in-line function that can be used to retrieve a value instead of the *GET command (see [Using In-line Get Functions](https://www.mm.bme.hu/~gyebro/files/ans_help_v182/ans_apdl/Hlp_P_APDL3_3.html#apdluseingettlm8599) for more information).\
*GET 获取指定项目的值，并将该值存储为标量参数或用户命名的数组参数值。项目可通过各种关键字、标签和数字组合来识别。使用方法与 *SET 命令类似，不同之处在于参数值是从先前的输入或计算结果中获取的。例如，*GET,A,ELEM,5,CENT,X 返回元素 5 的中心点 x 位置，并将结果存储为参数 A。获取函数是一种替代 *GET 命令的内联函数，可用于获取数值（更多信息请参阅使用内联获取函数）。

Both *GET and *VGET retrieve information from the active data stored in memory. The database is often the source, and sometimes the information is retrieved from common memory blocks that the program uses to manipulate information. Although POST1 and POST26 operations use a *.rst file, *GET data is accessed from the database or from the common blocks. Get operations do not access the *.rst file directly. For repeated gets of sequential items, such as from a series of elements, see the *VGET command.\
*GET 和 *VGET 都是从存储在内存中的活动数据中检索信息。数据库通常是信息源，有时信息是从程序用来处理信息的常用内存块中获取的。虽然 POST1 和 POST26 操作使用的是 *.rst 文件，但 *GET 数据是从数据库或公共块中访问的。获取操作不直接访问 *.rst 文件。要重复获取顺序项，如从一系列元素中获取，请参阅 *VGET 命令。

Most items are stored in the database after they are calculated and are available anytime thereafter. Items are grouped according to where they are usually first defined or calculated. Preprocessing data will often not reflect the calculated values generated from section data. Do not use *GET to obtain data from elements that use calculated section data, such as beams or shells. When the value retrieved by *GET is a component name, the resulting character parameter is limited to 32 characters. If the component name is longer than 32 characters, the remaining characters are ignored.\
大多数项目在计算后都会存储在数据库中，之后可随时使用。项目根据其通常首次定义或计算的位置分组。前处理数据通常不会反映由截面数据生成的计算值。不要使用 *GET 从使用计算截面数据的元素（如梁或壳）中获取数据。当 *GET 获取的值是一个组件名时，生成的字符参数限制为 32 个字符。如果组件名称长于 32 个字符，剩余的字符将被忽略。

Most of the general items listed below are available from all modules. Each of the sections for accessing *GET parameters are shown in the following order:\
所有模块都可以使用下面列出的大部分常规项目。访问 *GET 参数的各部分按以下顺序排列：

- *GET General Entity Items
- *GET Preprocessing Entity Items
- *GET Solution Entity Items
- *GET Postprocessing Entity Items

The *GET command is valid in any processor.

General Items
-----------




Examples
-------

Retrieve the number of nodes\
读取节点数

```python
>>> value = mapdl.get('val', 'node', '', 'count')
>>> value
3003
```

Retrieve the number of nodes using keywords. Note that the parameter name is optional.\
使用关键字参数读取节点数。请注意，参数名称是可选的。

```python
>>> value = mapdl.get(entity='node', item1='count')
>>> value
3003
```


````