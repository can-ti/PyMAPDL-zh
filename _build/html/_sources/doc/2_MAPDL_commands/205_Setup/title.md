# title

```{py:method} Mapdl.title(title='', **kwargs)

Defines a main title.

APDL Command: `/TITLE`

Parameters:
----------

  *title str*
  : Input up to 72 alphanumeric characters. Parameter substitution may be forced within the title by enclosing the parameter name or parametric expression within percent (%) signs.

Notes
------

The title is carried through the printout and written on various files. The title written to a file is the title defined at that time. Special characters may be used within the title text. Subtitles may also be defined [`/STITLE`].\
标题贯穿打印输出并写在各种文档上。写入文档的标题是当时定义的标题。标题文本中可以使用特殊字符。副标题也可以定义[`/STITLE`]。

This command is valid in any processor.

```
