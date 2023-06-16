# clear

````{py:method} Mapdl.clear(*args, **kwargs)

Clear the database.

APDL Command: `/CLEAR`

Notes
-------

Resets the ANSYS database to the conditions at the beginning of the problem. Sets the import and Boolean options back to the ANSYS default. All items are deleted from the database and memory values are set to zero for items derived from database information. All files are left intact. This command is useful between multiple analyses in the same run, or between passes of a multi-pass analysis (such as between the substructure generation, use, and expansion passes). Should not be used in a do-loop since loop counters will be reset. on the same line as the `/CLEAR` command.\
将 ANSYS 数据库重设为问题开始时的条件。将导入和布尔选项设置为 ANSYS 的默认值。所有的项目都从数据库中删除，对于从数据库信息中得到的项目，内存值被设置为零。所有的文件都保持原样。这个命令在同一运行中的多个分析之间，或者在一个多道分析的各道之间（如在子结构生成、使用和扩展之间）是很有用的。不应在 do 循环中使用，因为循环计数器将被重置。与 `/CLEAR` 命令位于同一行。。

`/CLEAR` resets the jobname to match the currently open session .LOG and .ERR files. This will return the jobname to its original value, or to the most recent value specified on `/FILNAME` with KEY = 1.\
`/CLEAR` 重置作业名称，以匹配当前打开的会话 .LOG 和 .ERR 文件。这将使作业名称返回到它的原始值，或返回到在 `/FILNAME` 上指定的最近的值，同时 KEY = 1。

This command is valid only at the Begin level.

Examples
-------

```py
>>> mapdl.clear()
```


````