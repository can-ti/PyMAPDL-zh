# rename

```{py:method} Mapdl.rename(fname1='', ext1='', fname2='', ext2='', distkey='', **kwargs)

Renames a file.

APDL Command: `/RENAME`

Parameters:
-----------

  *fname1*
  : The file to be renamed. You can also include an optional directory path as part of the specified file name; if not, the default file location is the working directory.\
  要重命名的文件。你也可以包括一个可选的目录路径作为指定文件名的一部分；如果没有，默认的文件位置是工作目录。

  *ext1*
  : Filename extension (eight-character maximum).

  *fname2*
  : The new name for the file. You can also include an optional directory path as part of the new file name; if not, the default is the working directory. A maximum of 248 characters is allowed for the file name (or combined file name and directory path, if both are specified).\
  该文件的新名称。你也可以包括一个可选的目录路径作为新文件名的一部分；如果没有，默认是工作目录。文件名最多允许248个字符（或合并文件名和目录路径，如果两者都被指定）。

  *ext2*
  Filename extension (eight-character maximum).

  *distkey*
  Key that specifies whether the rename operation is performed on all processes in distributed parallel mode (Distributed ANSYS):\
  指定重命名操作是否在分布式并行模式（分布式ANSYS）下对所有进程执行：
  1 (ON or YES) - The program performs the rename operation locally on each process.\
  0 (OFF or NO) - The program performs the rename operation only on the master process (default).

Notes
-------

Renames a file. Ex: /RENAME,A,,,B renames file A to B in the same directory. /RENAME,A,DAT,,,INP renames file A.DAT to A.INP. On all systems, this command will overwrite any existing file named B. See the Operations Guide for details. Only ANSYS binary files should be renamed. Use /SYS and system renaming commands for other files.\
重命名一个文件。例如：/RENAME,A,,B将同一目录下的文件A重命名为B。/RENAME,A,DAT,,INP将文件A.DAT重命名为A.INP。在所有的系统上，这个命令将覆盖任何现有的名为B的文件，详情请见操作指南。只有ANSYS的二进制文件应该被重命名。对其他文件使用/SYS和系统重命名命令。

In distributed parallel mode (Distributed ANSYS), only the master process will rename Fname1.Ext1 to Fname2.Ext2 by default. However, when DistKey is set to 1 (or ON or YES), the command is executed by all processes. In this case, Fname1 and Fname2 will automatically have the process rank appended to them. This means Fname1N.Ext1 will be renamed to Fname2N.Ext2 by all processes, where N is the Distributed ANSYS process rank. For more information see Differences in General Behavior in the Parallel Processing Guide.

Renaming across system partitions may be internally done by a copy and delete operation on some systems.

This command is valid only at the Begin Level.

```