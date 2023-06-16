# assigin

```{py:method} Mapdl.assign(ident='', fname='', ext='', lgkey='', **kwargs)

Reassigns a file name to an ANSYS file identifier.\
将一个文件名重新分配给 ANSYS 文件标识符。

APDL Command: `/ASSIGN`

parameters:
----------

  *ident*
  : ANSYS file name identifier. Valid identifiers are: CMS, EMAT, EROT, ESAV, FULL, LN07, LN09, LN11, LN20, LN21, LN22, LN25, LN31, LN32, MODE, OSAV, RDSP, RFRQ, RMG, RST, RSTP, RTH, SELD, and SSCR. See File Management and Files for file descriptions. If blank, list currently reassigned files.\
  ANSYS文件名标识符。有效的标识符是：CMS, EMAT, EROT, ESAV, FULL, LN07, LN09, LN11, LN20, LN21, LN22, LN25, LN31, LN32, MODE, OSAV, RDSP, RFRQ, RMG, RST, RSTP, RTH, SELD, and SSCR。文件描述见文件管理和文件。如果是空白，列出当前重新分配的文件。

  *fname*
  : File name and directory path (248 characters maximum, including the characters needed for the directory path). An unspecified directory path defaults to the working directory; in this case, you can use all 248 characters for the file name.\
  文件名和目录路径（最多 248 个字符，包括目录路径所需的字符）。未指定的目录路径默认为工作目录；在这种情况下，你可以使用所有 248 个字符的文件名。

  *ext*
  : Filename extension (eight-character maximum).

  *lgkey*
  : Key to specify local or global file name control for the specified file identifier in a distributed-memory parallel processing (Distributed ANSYS) run. For more information on local and global files, see File Handling Conventions in the Parallel Processing Guide.\
  键，在分布式内存并行处理（Distributed ANSYS）运行中为指定的文件标识符指定本地或全局文件名控制。关于本地 
  和全局文件的更多信息，见《并行处理指南》中的文件处理约定。\
  BOTH - Reassign the file name for both the local and global files (default).\
  LOCAL - Reassign the file name for only the local files.\
  GLOBAL - Reassign the file name for only the global file.

Notes
------

The reassignment of file names is valid only if it is done before the file is used. All file reassignments are retained (not cleared) even if the database is cleared [/CLEAR] or the Jobname is changed [/FILNAME]. Assigned files may be overwritten. If file name arguments (Fname, Ext, –) are blank, the default ANSYS assignment is restored. Use SEOPT for SUB files and SEEXP for DSUB files.\
文件名的重新分配只有在文件被使用之前进行才有效。即使数据库被清除[/CLEAR]或工作名称被改变[/FILNAME]，所有文件的重新分配都被保留（不被清除）。指定的文件可能会被覆盖。如果文件名参数（Fname, Ext, -）为空，则恢复 ANSYS 的默认分配。对 SUB 文件使用 SEOPT，对 DSUB 文件使用 SEEXP。

This command is valid only at the Begin Level.

This command also checks to ensure that the path/file is valid and can be written by the user. If it is not valid, an error message will be returned. Ensure that the directory exists prior to using /ASSIGN command.\
该命令还检查以确保路径/文件是有效的，并且可以由用户写入。如果无效，将返回一个错误信息。在使用/ASSIGN命令之前，请确保该目录存在。

```


