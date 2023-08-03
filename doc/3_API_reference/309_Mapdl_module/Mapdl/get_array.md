# get_array

````{method} Mapdl.get_array(entity='', entnum='', item1='', it1num='', item2='', it2num='', kloop='', **kwargs)

Uses the `*VGET`` command to Return an array from ANSYS as a Python array.\
使用 `*VGET`` 命令以 Python 数组形式从 ANSYS 返回数组。

See [*VGET](https://www.mm.bme.hu/~gyebro/files/ans_help_v182/ans_cmd/Hlp_C_VGET_st.html) for more detials.

Parameters:
------------

  *entity* 
  : Entity keyword. Valid keywords are NODE, ELEM, KP, LINE, AREA, VOLU, etc\
  实体关键字。有效的关键字包括 NODE、ELEM、KP、LINE、AREA、VOLU 等。

  *entnum*
  : The number of the entity.

  *item1*
  : The name of a particular item for the given entity. Valid items are as shown in the Item1 columns of the tables below.\
  给定实体的特定项目名称。有效项目如下表中 Item1 栏所示。

  *it1num*
  : The number (or label) for the specified Item1 (if any). Valid IT1NUM values are as shown in the IT1NUM columns of the tables below. Some Item1 labels do not require an IT1NUM value.\
  指定项目 1（如果有）的编号（或标签）。有效的 IT1NUM 值如下表 IT1NUM 列所示。某些 Item1 标签不需要 IT1NUM 值。

  *item2,it2num*
  : A second set of item labels and numbers to further qualify the item for which data is to be retrieved. Most items do not require this level of information.\
  第二组项目标签和编号，用于进一步限定要检索数据的项目。大多数项目不需要这一级别的信息。

  *kloop*
  : Field to be looped on: 要循环的字段：
  - 0 or 2 : Loop on the ENTNUM field (default).
  - 3 : Loop on the Item1 field.
  - 4 : Loop on the IT1NUM field. Successive items are as shown with IT1NUM.
  - 5 : Loop on the Item2 field.
  - 6 : Loop on the IT2NUM field. Successive items are as shown with IT2NUM.

*VGET Notes
--------

Retrieves values for specified items and stores the values in an output vector of a user-named array parameter according to:\
读取指定项目的值，并根据以下规则将这些值存储到用户命名的数组参数的输出向量中：

$$
ParR = f(Entity, ENTNUM, Item1, IT1NUM, Item2, IT2NUM)
$$

where (f) is the *GET function; Entity, Item1, and Item2 are keywords; and ENTNUM, IT1NUM, and IT2NUM are numbers or labels corresponding to the keywords. Looping continues over successive entity numbers (ENTNUM) for the KLOOP default. For example, *VGET,A(1),ELEM,5,CENT,X returns the centroid x-location of element 5 and stores the result in the first location of A. Retrieving continues with element 6, 7, 8, etc., regardless of whether the element exists or is selected, until successive array locations are filled. Use *VLEN or *VMASK to skip locations. Absolute values and scale factors may be applied to the result parameter (*VABS, *VFACT). Results may be cumulative (*VCUM). See the *VOPER command for general details. Results can be put back into an analysis by writing a file of the desired input commands with the *VWRITE command. See also the *VPUT command.\
其中 (f) 是 *GET 函数；实体、项目 1 和项目 2 是关键字；ENTNUM、IT1NUM 和 IT2NUM 是与关键字相对应的数字或标签。对于 KLOOP 默认值，循环会在连续的实体编号 (ENTNUM) 上继续。例如，*VGET,A(1),ELEM,5,CENT,X 返回元素 5 的中心点 x 位置，并将结果存储在 A 的第一个位置。使用 *VLEN 或 *VMASK 可以跳过位置。绝对值和比例因子可应用于结果参数（*VABS、*VFACT）。结果可以累计（*VCUM）。有关一般详情，请参阅 *VOPER 命令。使用 *VWRITE 命令写入所需的输入命令文件，可以将结果放回分析中。另请参阅 *VPUT 命令。

Both *GET and *VGET retrieve information from the active data stored in memory. The database is often the source, and sometimes the information is retrieved from common memory blocks that Mechanical APDL uses to manipulate information. Although POST1 and POST26 operations use a *.rst file, GET data is accessed from the database or from the common blocks. Get operations do not access the *.rst file directly.\
*GET 和 *VGET 都是从存储在内存中的活动数据中检索信息。数据库通常是信息源，有时信息是从 Mechanical APDL 用来操作信息的常用内存块中检索的。虽然 POST1 和 POST26 操作使用 *.rst 文件，但 GET 数据是从数据库或常用块中访问的。Get 操作不直接访问 *.rst 文件。

The *VGET command retrieves both the unprocessed real and the imaginary parts (original and duplicate sector nodes and elements) of a cyclic symmetry solution.\
*VGET 命令可检索循环对称解法的未处理实部和虚部（原始和重复扇形节点和元素）。

Each of the sections for accessing *VGET parameters are shown in the following order:\
访问 *VGET 参数的各个部分按以下顺序排列：

- *VGET PREP7 Items
- *VGET POST1 Items

Examples
--------

List the current selected node numbers\
列出当前选定的节点编号

```python
>>> mapdl.get_array('NODE', item1='NLIST')
array([  1.,   2.,   3.,   4.,   5.,   6.,   7.,   8.,
      ...
      314., 315., 316., 317., 318., 319., 320., 321.])
```

List the displacement in the X direction for the first result\
列出第一个结果的 X 方向位移值

```python
>>> mapdl.post1()
>>> mapdl.set(1, 1)
>>> disp_x = mapdl.get_array('NODE', item1='U', it1num='X')
array([ 0.01605306, -0.01605306,  0.00178402, -0.01605306,
       ...
       -0.00178402, -0.01234851,  0.01234851, -0.01234851])
```

````