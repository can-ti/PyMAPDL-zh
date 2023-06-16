# slashdelete

```{py:method} Mapdl.slashdelete(fname='', ext='', distkey='', **kwargs)

Deletes a file.

APDL Command: `/DELETE`

Parameters:
-------------

  *fname*
  : File name and directory path (248 characters maximum, including the characters needed for the directory path). An unspecified directory path defaults to the working directory; in this case, you can use all 248 characters for the file name.\
  文件名和目录路径（最多 248 个字符，包括目录路径所需的字符）。未指定的目录路径默认为工作目录；在这种情况下，你可以使用所有 248 个字符的文件名。

  *ext*
  : Filename extension (eight-character maximum).

  *distkey*
  : Key that specifies whether the file deletion is performed on all processes in distributed parallel mode (Distributed ANSYS):\
  指定在分布式并行模式（分布式 ANSYS）下是否对所有进程进行文件删除：
  1 (ON or YES) - The program performs the file deletion locally on each process.
  0 (OFF or NO) - The program performs the file deletion only on the master process (default).

Notes
-------

In distributed parallel mode (Distributed ANSYS), only the master process will delete Fname.Ext by default. However, when DistKey is set to 1 (or ON or YES), the command is executed by all processes. In this case, Fname will automatically have the process rank appended to it. This means FnameN.Ext will be deleted by all processes, where N is the Distributed ANSYS process rank. For more information see Differences in General Behavior in the Parallel Processing Guide.\
在分布式并行模式下（分布式 ANSYS），默认情况下只有主进程会删除 Fname.Ext。然而，当 DistKey 被设置为 1（或 ON 或 YES）时，该命令将由所有进程执行。在这种情况下，Fname 将自动有进程等级附加到它上面。这意味着 FnameN.Ext 将被所有进程删除，其中 N 是分布式 ANSYS 进程的等级。更多信息请参见《并行处理指南》中的一般行为的差异。


```