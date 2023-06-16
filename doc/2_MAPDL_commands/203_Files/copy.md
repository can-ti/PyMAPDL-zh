# copy

```{py:method} Mapdl.copy(fname1='', ext1='', fname2='', ext2='', distkey='', **kwargs)

Copies a file:

APDL Command: `/COPY`

Parameters:
-----------

  *fname1*
  : File name to be copied and its directory path (248 characters maximum for both file name and directory). If you do not specify a directory path, it will default to your working directory and you can use all 248 characters for the file name.

  *ext1*
  : Filename extension (eight-character maximum).

  *fname2*
  : File name to be created and its directory path (248 characters maximum for both file name and directory). If you do not specify a directory path, it will default to your working directory and you can use all 248 characters for the file name.

  *ext2*
  : Filename extension (eight-character maximum).

  *distkey*
  : Key that specifies whether the copy operation is performed on all processes in distributed parallel mode (Distributed ANSYS):\
指定是否在分布式并行模式（分布式 ANSYS）下对所有进程进行复制操作：
0 (OFF or NO) - The program performs the copy operation only on the master process (default).
1 (ON or YES) - The program performs the copy operation locally on each process.
2 or BOTH - The program performs the copy operation for Fname.Ext on the master process and for FnameN.Ext on all processes.

Notes
--------

The original file is untouched. Ex: /COPY,A,,,B copies file A to B in the same directory. /COPY,A,DAT,,,INP copies the file A.DAT to A.INP. See the Operations Guide for details. ANSYS binary and ASCII files can be copied.\
原始文件不动。例如：`/COPY,A,,B` 复制文件 A 到同一目录下的 B。`/COPY,A,DAT,,INP`将文件 A.DAT 复制到 A.INP。详见操作指南。ANSYS 的二进制和 ASCII 文件可以被复制。

In distributed parallel mode (Distributed ANSYS), only the master process will copy Fname1.Ext1 to Fname2.Ext2 by default. However, when DistKey is set to 1 (or ON or YES), the command is executed by all processes. In this case, Fname1 and Fname2 will automatically have the process rank appended to them. This means Fname1N.Ext1 will be copied to Fname2N.Ext2 by all processes, where N is the Distributed ANSYS process rank. For more information see Differences in General Behavior in the Parallel Processing Guide.\
在分布式并行模式下（分布式 ANSYS），默认情况下只有主进程会将 Fname1.Ext1 复制到 Fname2.Ext2。然而，当 DistKey 被设置为1（或 ON 或 YES）时，该命令将由所有进程执行。在这种情况下，Fname1 和 Fname2 将自动附加上进程的等级。这意味着 Fname1N.Ext1 将被所有进程复制到 Fname2N.Ext2，其中 N 是分布式 ANSYS 进程等级。更多信息请参见《并行处理指南》中的一般行为的差异。

```