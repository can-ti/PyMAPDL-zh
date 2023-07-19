# esel

````{py:method} Mapdl.esel(type_='', item='', comp='', vmin='', vmax='', vinc='', kabs='', **kwargs)

Selects a subset of elements.

APDL Command: `ESEL`

Parameters:
--------

  *type_*
  : Label identifying the type of select:
  - S - Select a new set (default).
  - R - Reselect a set from the current set.
  - A - Additionally select a set and extend the current set.
  - U - Unselect a set from the current set.
  - ALL - Restore the full set.
  - NONE - Unselect the full set.
  - INVE - Invert the current set (selected becomes unselected and vice versa(反之亦然)).
  - STAT - Display the current select status.

The following fields are used only with *Type* = S, R, A, or U:

  *item*
  : Label identifying data, see [Table 7: `ESEL` - Valid Item and Component Labels](Valid-Item-and-Component-Labels-of-ESEL) Some items also require a component label. Defaults to ELEM. If *Item* = STRA (straightened), elements are selected whose midside nodes do not conform to the curved line or non-flat area on which they should lie. (Such elements are sometimes formed during volume meshing (`VMESH`) in an attempt to avoid excessive element distortion.) You should graphically examine any such elements to evaluate their possible effect on solution accuracy.\
标签识别数据，见[表7：`ESEL`-有效的 item 和 component 标签](Valid-Item-and-Component-Labels-of-ESEL)。有些项目还需要一个组件标签。默认为 ELEM。如果 *Item* = STRA（straightened），则会选择那些中间节点不符合曲线或不平坦区域的元素。（这样的元素有时会在体积网格划分（`VMESH`）过程中形成，以试图避免过度的单元变形）。你应该以图形方式检查任何这样的单元，以评估它们对求解结果准确性的影响。

  *comp*
  : Component of the item (if required). Valid component labels are shown in Table 110: ESEL - Valid Item and Component Labels below.

  *vmin*
  : Minimum value of item range. Ranges are element numbers, attribute numbers, load values, or result values as appropriate for the item. A component name (as specified via the `CM` command) can also be substituted for *VMIN* (in which case *VMAX* and *VINC* are ignored).\
  *item* 范围的最小值。范围是元素数、属性数、加载值或结果值，视 *item* 的情况而定。一个组件名称（通过 `CM` 命令指定）也可以代替 *VMIN*（在这种情况下， *VMAX* 和 *VINC* 被忽略）。

  *vmax*
  : Maximum value of item range. *VMAX* defaults to *VMIN* for input values. For result values, *VMAX* defaults to infinity if *VMIN* is positive, or to zero if *VMIN* is negative.

  *vinc*
  : Value increment within range. Used only with integer ranges (such as for element and attribute numbers). Defaults to 1. *VINC* cannot be negative.

  *kabs*
  : Absolute value key:
  - 0 — Check sign of value during selection.\在选择过程中检查值的标志。
  - 1 — Use absolute value during selection (sign ignored).\选择时使用绝对值（忽略符号）。

Return type:
----------

  `Optional`[`str`]

Notes
-------

The fields *item*, *comp*, *vmin*, *vmax*, *vinc* and *kabs* are used only with *type_ = “S”, “R”, “A”, or “U”*.

Selects elements based on values of a labeled item and component. For example, to select a new set of elements based on element numbers 1 through 7, use

```py
>>> mapdl.esel('S', 'ELEM', '', 1, 7)
```

The subset is used when the ALL label is entered (or implied) on other commands, such as\
当在其他命令中输入（或隐含）ALL标签时，会使用该子集，例如

```py
>>> mapdl.elist('ALL')
```

Only data identified by element number are selected. Selected data are internally flagged; no actual removal of data from the database occurs. Different element subsets cannot be used for different load steps (`SOLVE`) in a `/SOLU` sequence. The subset used in the first load step is used for all subsequent load steps regardless of subsequent `ESEL` specifications.\
只有按单元编号确定的数据被选中。被选择的数据在内部被标记，实际上并没有从数据库中删除数据。不同的单元子集不能用于 `/SOLU` 序列中的不同荷载步（`SOLVE`）。在第一个荷载步中使用的子集被用于所有后续的加载步骤，与后续的`ESEL'规格无关。

This command is valid in any processor.

Elements crossing the named path (`PATH`) are selected. This option is available only in **PREP7** and **POST1**. If no geometry data has been mapped to the path (via `PMAP` and `PDEF`, for example), the path assumes the default mapping option (`PMAP,UNIFORM`) to map the geometry prior to selecting the elements. If an invalid path name is given, the `ESEL` command is ignored (and the status of selected elements is unchanged). If no elements are crossing the path, the `ESEL` command returns zero elements selected.\
越过指定路径（`PATH`）的元素被选中。这个选项只在 **PREP7** 和 **POST1** 中可用。如果没有几何数据被映射到路径上（例如通过 `PMAP' 和 `PDEF' ），路径会假定默认的映射选项（`PMAP,UNIFORM`），在选择元素之前映射几何。如果给了一个无效的路径名称，`ESEL` 命令将被忽略（所选元素的状态不变）。如果没有元素穿过路径，`ESEL'命令返回零个选择的元素。

For selections based on non-integer numbers (coordinates, results, etc.), items that are within the range *VMIN* - *Toler* and *VMAX* + *Toler* are selected. The default tolerance *Toler* is based on the relative values of *VMIN* and *VMAX* as follows:\
对于基于非整数的选择（坐标、结果等），在*VMIN*-*Toler*和*VMAX*+*Toler*范围内的*item*被选中。默认的公差*Toler*是基于*VMIN*和*VMAX*的相对值，如下所示：

- If *VMIN* = *VMAX*, *Toler* = 0.005 x *VMIN*.
- If *VMIN* = *VMAX* = 0.0, *Toler* = 1.0E-6.
- If *VMAX* ≠ *VMIN*, *Toler* = 1.0E-8 x (*VMAX* - *VMIN*).

To override this default and specify *Toler* explicitly, issue the `SELTOL` command.\
要更改这个默认值并明确指定的 *Toler*，请发出 `SELTOL` 命令。


% 注意表名里面不能有空格
```{table} ESEL - Valid Item and Component Labels
:name: Valid-Item-and-Component-Labels-of-ESEL 


| Item | Comp | Description |
| --- | --- | --- |
| ELEM |  | Element number. |
| ADJ |  | Elements adjacent(/əˈdʒeɪsnt/ 临近的) to element *VMIN* (*VMAX* and *VINC* fields are ignored). Only elements (of the same dimensionality) adjacent to lateral faces are considered. Progression continues until edge of model or until more than two elements are adjacent at a face.\与元素*VMIN*相邻的元素(*VMAX*和*VINC*区域被忽略)。只考虑与横向面相邻的元素（尺寸相同）。进展一直持续到模型的边缘或在一个面上有两个以上的元素相邻为止。|
| CENT | X,Y,Z | X, Y, or Z location in the active coordinate system. |
| TYPE |  | Element type number. |
| ENAME |  | Element name (or identifying number). |
| MAT |  | Material ID number. |
| REAL | (blank) | Real constant number. |
|  | GCN | General contact/target elements (select all elements identified by real constant set number = 0). Remaining fields (*VMIN*, *VMAX*, etc.) are ignored.\一般接触/目标元素(选择所有由实数常数集编号=0确定的元素)。其余的字段（*VMIN*，*VMAX*，等等）被忽略。|
|  | BASE | All split contact pairs (`CNCHECK,SPLIT/DMP`) that are associated with the current real constant set number.\所有与当前实数组编号相关的分割接触对（`CNCHECK,SPLIT/DMP`）。|
| ESYS |  | Element coordinate system number. |
| OVER |  | Overlapping contact elements created during contact pair splitting (`CNCHECK,SPLIT/DMP`)\在拆分接触对时产生的重叠接触单元(`CNCHECK,SPLIT/DMP`)|
| LIVE |  | Active elements (`EALIVE`). *VMIN* and *VMAX* fields are ignored. |
| LAYER |  | Layer number (where only composite elements with a nonzero thickness for the requested layer number are included)(`LAYER`).\层编号（其中只包括所要求的层数的厚度不为零的复合元素）（`LAYER`）。|
| SEC | (blank) | Cross section ID number (`SECNUM`) |
|  | MAT | Selects the elements with the requested MAT ID specified via *VMIN* and *VMAX* as attached to the section. |
| STRA |  | Straightened. See the description of the *Item* argument above. |
| SFE | PRES | Element pressure. |
|  | CONV | Element convection bulk temperature.元素对流体积温度。 |
|  | HFLUX | Element heat flux.单元热通量。 |
|  | FSI | Element (acoustic) fluid-structure interaction flag.元素（声学）流体-结构相互作用的标志。 |
|  | IMPD | Element (acoustic) impedance. |
|  | SHLD | Surface normal velocity or acceleration (acoustic analysis). |
|  | MXWF | Element Maxwell force flag. |
|  | CHRGS | Electric surface charge density. |
|  | INF | Element infinite surface flag. |
|  | DFLUX | Element diffusion flux. |
| BFE | TEMP | Element temperature. |
|  | FLUE | Element fluence. |
|  | HGEN | Element heat generation rate. |
|  | JS | Element current density, magnitude only. |
|  | MVDI | Element magnetic virtual displacements flag. |
|  | DGEN | Element diffusing substance generation rate. |
|  | CHRGD | Electric charge density. |
| PATH | *Lab* | Selects all elements being crossed by the path with name *Lab*(`PATH`). If *Lab* = ALL, all elements related to all defined paths are selected. |
| ETAB | *Lab* | Any user-defined element table label (`ETABLE`). |

```

Examples
--------

Select elements using material numbers 2, 4 and 6.

```py
>>> mapdl.esel('S', 'MAT', '', 2, 6, 2)
```

Of these, reselect SOLID185 element types

```py
>>> mapdl.esel('R', 'ENAME', '', 185)
```

Select elements assigned to material property 2

```py
>>> mapdl.esel('S', 'MAT', '', 2)
```

Note, this command is equivalent to:

```py
>>> mapdl.esel('S', 'MAT', vmin=2)
```


````

