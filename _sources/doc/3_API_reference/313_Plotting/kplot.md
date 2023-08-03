# kplot

````{method} Mapdl.kplot(np1='', np2='', ninc='', lab='', vtk=None, show_keypoint_numbering=True, **kwargs)

Display the selected keypoints.

APDL Command: `KPLOT`

```{note}
PyMAPDL plotting commands with `vtk=True` ignore any values set with the `PNUM` command.\
使用 `vtk=True` 的 PyMAPDL 绘图命令会忽略使用 `PNUM` 命令设置的任何值。
```

Parameters:
------------

  np1,np2,ninc
  : Display keypoints from NP1 to NP2 (defaults to NP1) in steps of NINC (defaults to 1). If NP1 = ALL (default), NP2 and NINC are ignored and all selected keypoints [KSEL] are displayed.\
  以 NINC（默认为 1）为步长显示从 NP1 到 NP2（默认为 NP1）的关键点。如果 NP1 = ALL（默认值），则忽略 NP2 和 NINC，显示所有选定的关键点 [KSEL]。

  lab
  : Determines what keypoints are plotted (one of the following):\
  确定绘制的关键点（以下之一）：
  - (blank) - Plots all keypoints.(绘制所有关键点。)
  - HPT - Plots only those keypoints that are hard points.(只绘制那些关键的应电。)

  vtk : *`bool`* , *`optional`*
  : Plot the currently selected lines using `pyvista`.

  show_keypoint_numbering : *`bool`* , *`optional`*
  : Display keypoint numbers when `vtk=True`.

Notes
------

This command is valid in any processor.

````