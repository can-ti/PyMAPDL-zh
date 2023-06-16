# slashfdele

````{py:method} Mapdl.slashfdele(ident='', stat='', **kwargs)

Deletes a binary file after it is used.\
在一个二进制文件被使用后将其删除。

APDL Command: `/FDELE`

Parameters:
------------

  *ident*
  : ANSYS file name identifier. Valid identifiers are: EMAT, ESAV, FULL, SUB, MODE, DSUB, USUB, OSAV, and SELD. See the Basic Analysis Guide for file descriptions.\
  ANSYS 文件名标识符。有效的标识符是：EMAT, ESAV, FULL, SUB, MODE, DSUB, USUB, OSAV, 和 SELD。关于文件的描述，请参见《基本分析指南》。

  *stat*
  : Keep or delete key:\
  KEEP - Keep this file.\
  DELE - Delete (or do not write, if not necessary) this file.

Notes
-------

Deletes as soon as possible (or prevents writing) a binary file created by the ANSYS program to save space.\
尽快删除（或防止写入）由ANSYS程序创建的二进制文件以节省空间。

```{warning}
Deleting files that are necessary for the next substep, load step, or analysis will prevent continuation of the run.\
删除下一个子步骤、加载步骤或分析所需的文件将阻止运行的继续。
```

This command is valid only at the Begin Level.

````