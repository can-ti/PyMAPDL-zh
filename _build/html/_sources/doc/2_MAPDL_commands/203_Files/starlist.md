# starlist

```{py:method} Mapdl.starlist(fname='', ext='', **kwargs)

Displays the contents of an external, coded file.\
显示一个外部的编码文件的内容。

APDL Command: `*LIST`

Parameters:
----------

  *fname*
  : File name and directory path (248 characters maximum, including the characters needed for the directory path). An unspecified directory path defaults to the working directory; in this case, you can use all 248 characters for the file name.\
  文件名和目录路径（最多248个字符，包括目录路径所需的字符）。未指定的目录路径默认为工作目录；在这种情况下，你可以使用所有248个字符的文件名。

  *ext*
  : Filename extension (eight-character maximum).

Notes
----------

Displays the contents of an external, coded file. The file to be listed cannot be in use (open) at the time (except for the error file, File.ERR, which may be displayed with `*LIST,ERR`).\
显示一个外部的编码文件的内容。要列出的文件当时不能正在使用（打开）（除了错误文件 File.ERR，它可以用 `*LIST,ERR`显示）。

This command is valid in any processor.

```