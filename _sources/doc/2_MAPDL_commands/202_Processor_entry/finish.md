# finish

```{py:method} Mapdl.finish(**kwargs)

Exits normally from a processor.\
从一个处理器中正常退出。

APDL Command: `FINISH`

Notes
----------

Exits any of the ANSYS processors or the DISPLAY program. For the ANSYS processors, data will remain intact in the database but the database is not automatically written to a file (use the SAVE command to write the database to a file). See also the /QUIT command for an alternate processor exit command. If exiting POST1, POST26, or OPT, see additional notes below.\
退出任何一个 ANSYS 处理程序或 DISPLAY 程序。对于 ANSYS 处理器，数据库中的数据将保持不变，但数据库不会自动写入文件（使用 SAVE 命令将数据库写入文件）。另一个处理器退出命令请参见 /QUIT 命令。如果退出 POST1、POST26 或 OPT，请参阅下面的附加说明。

POST1: Data in the database will remain intact, including the POST1 element table data, the path table data, the fatigue table data, and the load case pointers.\
POST1：数据库中的数据将保持不变，包括 POST1 单元表数据、路径表数据、疲劳表数据和荷载情况标志。

POST26: Data in the database will remain intact, except that POST26 variables are erased and specification commands (such as FILE, PRTIME, NPRINT, etc.) are reset. Use the `/QUIT` command to exit the processor and bypass these exceptions.\
POST26：数据库中的数据将保持不变，除了 POST26 变量被擦除，规范命令（如FILE、PRTIME、NPRINT等）被重置。可以使用 `/QUIT` 命令退出处理器并绕过这些异常情况。

This command is valid in any processor. This command is not valid at the Begin level.


```