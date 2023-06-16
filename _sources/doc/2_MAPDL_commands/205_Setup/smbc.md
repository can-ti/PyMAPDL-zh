# smbc

```{py:method} Mapdl.smbc(mode='', **kwargs)

Controls the display of solid model boundary condition symbols and labels.\
控制实体模型边界条件符号和标签的显示。

APDL Command: `/SMBC`

Parameters:
------------

  *mode*
  : *CENT* 
    : Solid model boundary condition symbols and labels appear at the **centroid** of the solid model entity (default).\
  实体模型的边界条件符号和标签出现在实体模型实体的中心点（默认）。
    
    *TESS*
    : Solid model boundary condition symbols and labels appear inside each constituent element of the **tessellation**.\
    实体模型的边界条件符号和标签出现在方块图的每个组成元素内。

Notes
------

*Mode* = CENT is designed to reduce the clutter of boundary condition symbols in solid model plots. For example, if you have assigned normal pressure loads to an area, you may choose to display the pressures as arrows with the /PSF command using /PSF,PRES,NORM,2. When Mode = CENT, the pressure arrow is displayed at the centroid of the area. When Mode = TESS, a pressure arrow is displayed at the centroid of each polygon of the area’s tessellation.\
*Mode* = CENT 是为了减少实体模型中边界条件符号的混乱。例如，如果你给一个区域分配了正常压力载荷，你可以选择用 `/PSF` 命令用 `/PSF,PRES,NORM,2` 将压力显示为箭头。当 *Mode* = CENT 时，压力箭头显示在该区域的中心点。当 *Mode* = TESS时，压力箭头显示在该区域的每个多边形的中心点上。

This command is valid in any processor.

```