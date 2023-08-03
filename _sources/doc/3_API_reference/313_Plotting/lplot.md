# lplot

````{method} Mapdl.lplot(nl1='', nl2='', ninc='', vtk=None, show_line_numbering=True, show_keypoint_numbering=False, color_lines=False, **kwargs)

Display the selected lines.

APDL Command: `LPLOT`

```{note}
PyMAPDL plotting commands with `vtk=True` ignore any values set with the `PNUM` command.
```

Parameters:
------------

  n1,n2,ninc
  : Display lines from NL1 to NL2 (defaults to NL1) in steps of NINC (defaults to 1). If NL1 = ALL (default), NL2 and NINC are ignored and display all selected lines [LSEL].\
  以 NINC（默认为 1）为步长，显示从 NL1 到 NL2（默认为 NL1）的行。如果 NL1 = ALL（默认值），则忽略 NL2 和 NINC，显示所有选定行 [LSEL]。

  vtk : *`bool`* , *`optional`*
  : Plot the currently selected lines using `pyvista`.

  show_line_numbering : *`bool`* , *`optional`*
  : Display line and keypoint numbers when `vtk=True`.

  show_keypoint_numbering : *`bool`* , *`optional`*
  : Number keypoints. Only valid when `show_keypoints=True`.

  **kwargs
  : See {doc}`ansys.mapdl.core.plotting.general_plotter() <../313_Plotting/general_plotter>` for more keyword arguments applicable when visualizing with `vtk=True`.

Notes
-------

Mesh divisions on plotted lines are controlled by the `ldiv` option of the `psymb` command when `vtk=False`. Otherwise, line divisions are controlled automatically.\
当 `vtk=False` 时，绘制线条上的网格划分由 `psymb` 命令的 `ldiv` 选项控制。否则，将自动控制网格线的划分。

This command is valid in any processor.

Examples
-------

```python
>>> mapdl.lplot(vtk=True, cpos='xy', line_width=10)
```


````