# stitle

```{py:method} Mapdl.stitle(nline='', title='', **kwargs)

Defines subtitles.

APDL Command: `/STITLE`

Parameters:
--------

  *nline*
  : Subtitle line number (1 to 4). Defaults to 1.

  *title*
  : Input up to 70 alphanumeric characters. Parameter substitution may be forced within the title by enclosing the parameter name or parametric expression within percent (`%`) signs. If Title is blank, this subtitle is deleted.\
  最多输入 70 个字母数字字符。通过将参数名称或参数表达式括在百分号（`%`）内，可以在标题中强制替换参数。如果标题为空，则删除此副标题。

Notes
------

Subtitles (4 maximum) are displayed in the output along with the main title [`/TITLE`]. Subtitles do not appear in GUI windows or in ANSYS plot displays. The first subtitle is also written to various ANSYS files along with the main title. Previous subtitles may be overwritten or deleted. Issue `/STATUS` to display titles.\
副标题（最多 4 个）与主标题 [`/TITLE`] 一起显示在输出中。字幕不会出现在 GUI 窗口或 ANSYS 绘图显示中。第一个副标题也与主标题一起写入各种 ANSYS 文档。以前的副标题可能会被覆盖或删除。发出 `/STATUS` 以显示标题。

This command is valid in any processor.

```

