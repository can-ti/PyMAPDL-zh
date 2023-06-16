# fcomp

```{py:method} Mapdl.fcomp(ident='', level='', **kwargs)

Specifies file compression level.\
指定文件压缩。

Parameters:
----------

  *ident*
  : ANSYS file name identifier. Input the label RST to compress the following results files: .RST, .RSTP, .RTH, and .RMG. See File Management and Files for file descriptions.\
  ANSYS 文件名标识符。输入标签 RST 来压缩以下结果文件：.RST, .RSTP, .RTH, 和.RMG。
  *level*
  : Compression level. Valid input values are 0 (no compression - default) to 5 (maximum compression).\
  压缩等级。有效的输入值是0（无压缩 - 默认）到5（最大压缩）。

Notes
-------

Command Default File compression is not performed.\
命令 默认不执行文件压缩。

Specifies file compression for results files (.RST, .RSTP, .RTH, and .RMG files). Records are compressed as they are written and uncompressed as they are read (for example, by the SET command).

See File Compression in the Basic Analysis Guide for more details.

```
