# lgwrite

````{py:method} Mapdl.lgwrite(fname='', ext='', kedit='', remove_grpc_extra=True, **kwargs)

Writes the database command log to a file.

APDL Command: `LGWRITE`

Parameters:

  *fname* : `str`,`optional`
  : File name and directory path (248 characters maximum, including the characters needed for the directory path). An unspecified directory path defaults to the working directory; in this case, you can use all 248 characters for the file name.\
  文件名和目录路径（最多248个字符，包括目录路径所需的字符）。未指定的目录路径默认为工作目录；在这种情况下，你可以使用所有248个字符的文件名。\
  The file name defaults to Jobname.

  *ext* : `str`,`optional`
  : Filename extension (eight-character maximum).

  *kedit* : `str`,`optional`
  : Flag to suppress nonessential commands:\
  抑制非必要的命令的标志：
  - `"NONE"` - Do not suppress any commands (default). 不压制任何命令（默认）。
  - `"COMMENT"` - Write nonessential commands as comments (starting with !). 将非必要的命令写成注释（以！开头）。
  - `"REMOVE"` - Do not write nonessential commands or comments. 不写入非必要的命令或注释。

  *remove_grpc_extra* :`bool`, *default* : `True`
  : Remove gRPC related content (like /OUT,anstmp). This will be ignored when MAPDL is not in gRPC mode.\
  删除 gRPC 相关的内容（如 `/OUT,anstmp`）。当 MAPDL 不处于 gRPC 模式时，这将被忽略。

Notes
-------

Writes the database command log to a named file. The database command log contains all commands that were used to create the current database. These commands are recorded in the database as they are issued, and saved in the database file (File.DB) whenever the database is saved. The `LGWRITE` command extracts these commands from the database and writes them to a file. Nonessential commands (for listing, graphics displays, help, etc.) can be excluded from the file by using the *Kedit* field. The file resulting from `LGWRITE` can be used as command input to the program. This command is most useful if the session log file (File.LOG), which is normally saved during an interactive session, has been lost or corrupted.\
将数据库命令日志写到一个命名的文件中。数据库命令日志包含用于创建当前数据库的所有命令。这些命令在发出时被记录在数据库中，并在保存数据库时被保存在数据库文件（File.DB）中。`LGWRITE` 命令从数据库中提取这些命令并将其写入文件中。非必要的命令（用于列表、图形显示、帮助等）可以通过使用 *Kedit* 字段从文件中排除。由 `LGWRITE` 产生的文件可以作为程序的命令输入。如果通常在交互式会话中保存的会话日志文件（File.LOG）已经丢失或损坏，这个命令是最有用的。

This command is valid in any processor.

Example
-------

Output the database command log to the local directory.\
输出数据库命令日志到本地目录。

```py
>>> import os
>>> mapdl.prep7()
>>> mapdl.k(1, 0, 0, 0, mute=True)
>>> mapdl.k(2, 2, 0, 0)
>>> filename = os.path.join(os.getcwd(), 'log.txt')
>>> mapdl.lgwrite(filename, kedit='REMOVE')
```

Print the output from the log file.
打印日志文件的输出。

```py
>>> with open(filename) as fid:
    lines = fid.readlines()
>>> print(''.join(lines))
/BATCH
/PREP7,
K,1,0,0,0
K,2,2,0,0
```

````