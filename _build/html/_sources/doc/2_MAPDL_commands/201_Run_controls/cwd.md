# cwd

````{py:method} Mapdl.cwd(dirpath='', **kwargs)

改变当前工作目录。

`dirpath` 不能包含任何单引号(\')/反引号(\`)。APDL中不支持这些。

APDL Command: /CWD

Parameters:
-------------

  *dirpath*
  : 新工作目录的完整路径名称。

Notes
------------

发出 */CWD* 命令后，所有没有指定默认目录的新文件（例如通过 *FILE,/COPY* 或 *RESUME* 命令）都默认为新的`dirpath` 目录。

Examples
------------

将 MAPDL 的工作目录改为 `"C:/temp"`。假定 MAPDL 在 Windows 上运行。

```py
>>> mapdl.cwd("C:/temp")
```

MAPDL on Linux example:

```py
>>> mapdl.cwd("/tmp/")
```

````

---------------------------


````{py:method} Mapdl.cwd(dirpath='', **kwargs)

Changes the current working directory.

`dirpath` must not contain any singular quotations/apostrophes. These are not supported in APDL.

APDL Command: /CWD

Parameters:
-------------

  *dirpath*
  : The full path name of the new working directory.

Notes
------------

After issuing the /CWD command, all new files opened with no default directory specified (via the *FILE,/COPY*, or *RESUME* commands, for example) default to the new `dirpath` directory.

Examples
------------

Change MAPDL’s working directory to `"C:/temp"`. This assumes that MAPDL running on Windows.

```py
>>> mapdl.cwd("C:/temp")
```

MAPDL on Linux example:

```py
>>> mapdl.cwd("/tmp/")
```

````