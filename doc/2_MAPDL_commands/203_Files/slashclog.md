# slashclog

```{py:method} Mapdl.slashclog(fname='', ext='', **kwargs)

APDL Command: `/CLOG`

Copies the session log file to a named file.\
将会话日志文件复制到一个已命名的文件。

Parameters:
-----------

  *fname*
  :File name and directory path to which the log file is to be copied (248 characters maximum, including directory). If you do not specify a directory path, it will default to your working directory and you can use all 248 characters for the file name.

  *ext*
  Filename extension (eight-character maximum).

Notes
-----

This command is valid in any processor, but only during an interactive run.

```