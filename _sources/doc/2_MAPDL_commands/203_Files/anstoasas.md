# anstoasas

```{py:method} Mapdl.anstoasas(fname='', key='', **kwargs)

Creates an ASAS input file from the current ANSYS model.

APDL Command: `ANSTOASAS`

Parameters:
-----------

  *fname*
  : ASAS file name. Defaults to Jobname.

  *key*
  : Key indicating type of file to produce:\
  0 - ASAS file for use by ANSYS Aqwa (no loads written). Creates the file Fname.asas.\
  1 - ASAS file (all data written, including loads). Creates the file Fname.asas.\
  2 - ASAS(NL) file. Creates the file Fname.asnl.

Notes
----

This command creates an input file for the ANSYS Asas Finite Element Analysis System from the model and loads currently in the database, based on the currently selected set of elements. Most common structural element types are written, as well as sections (or real constants), materials, boundary conditions and loads, and solution and load step options.
该命令根据当前选定的元素集，从当前数据库中的模型和载荷为 ANSYS Asas 有限元分析系统创建一个输入文件。大多数常见的结构元素类型会被写入，还有截面（或实际常数）、材料、边界条件和载荷，以及求解和载荷步骤选项。

更详细的内容可以去看本地帮助.

```