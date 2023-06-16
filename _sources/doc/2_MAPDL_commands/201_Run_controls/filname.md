# filname

```{py:method} Mapdl.filname(fname='', key='', **kwargs)

改变分析的工作名称。

APDL Command: /FILNAME

Parameters:
----------------

  *fname*
  : 作为工作名的名称（最多 32 个字符）。默认为 ANSYS 执行命令中指定的初始 Jobname，如果没有指定，则默认为 `file`。

  *key*
  : 指定是否使用现有的 log, error, lock, page 和 output 文件（.LOG、.ERR、.LOCK、.PAGE和.OUT）或启动新文件。
    - 0, OFF - 继续使用当前的 log, error, lock, page 和 output 文件。
    - 1, ON - 启动新的 log, error, lock, page 和 output 文件。\
    （旧的 log 和 error 文件被关闭和保存，但旧的 lock、page 和 output 文件会被删除）。现有的 log 和 error 文件会被追加。

Notes
------------
如果 `Key = 0`，所有随后创建的文件将以这个 Jobname 命名。 使用 `Key = 1` 来启动新的日志、错误、锁定、页面和输出文件。前一个 Jobname 通常在 ANSYS 程序执行行中定义（见操作指南）。当整个运行过程中创建的不同的文件组要有不同的名字时，这个命令很有用。例如，该命令可以在每个子结构传递之前使用，以避免覆盖文件或不得不单独重命名每个文件。

这条命令只在 Begin 层有效。





-------------------

```{py:method} Mapdl.filname(fname='', key='', **kwargs)

Changes the Jobname for the analysis.

APDL Command: /FILNAME

Parameters:
----------------

  *fname*
  : Name (32 characters maximum) to be used as the Jobname. Defaults to the initial Jobname as specified on the ANSYS execution command, or to file if none specified.

  *key*
  : Specify whether to use the existing log, error, lock, page, and output files (.LOG, .ERR, .LOCK, .PAGE and .OUT) or start new files.
    - 0, OFF - Continue using current log, error, lock, page, and output files.
    - 1, ON - Start new log, error, lock, page, and output files\
    (old log and error files are closed and saved, but old lock, page, and output files are deleted). Existing log and error files are appended.

Notes
------------
All subsequently created files will be named with this Jobname if Key = 0. Use Key = 1 to start new log, error, lock, page, and output files. The previous Jobname is typically defined on the ANSYS program execution line (see the Operations Guide). This command is useful when different groups of files created throughout the run are to have different names. For example, the command may be used before each substructure pass to avoid overwriting files or having to rename each file individually.

This command is valid only at the Begin level.

