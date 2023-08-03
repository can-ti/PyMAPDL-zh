# open_gui

````{method} Mapdl.open_gui(include_result=None, inplace=None)

Save the existing database and open it up in the MAPDL GUI.\
保存现有数据库并在 MAPDL GUI 中打开。

Parameters:
-------------

  include_result : *`bool`* , *`optional`*
  : Allow the result file to be post processed in the GUI. It is ignored if `inplace` is `True`. By default, `True`.\
  允许在图形用户界面中对结果文件进行后处理。如果 `inplace` 为 `True`，它将被忽略。默认为 `True`。

  inplace : *`bool`* , *`optional`*
  : Open the GUI on the current MAPDL working directory, instead of creating a new temporary directory and coping the results files over there. If `True`, ignores `include_result` parameter. By default, this `False`.\
  在当前 MAPDL 工作目录下打开图形用户界面，而不是创建一个新的临时目录并将结果文件复制到该目录下。如果为 `True`，则忽略 `include_result` 参数。默认为 `False`。

Examples
---------

```python
>>> from ansys.mapdl.core import launch_mapdl
>>> mapdl = launch_mapdl()
```

Create a square area using keypoints.

```python
>>> mapdl.prep7()
>>> mapdl.k(1, 0, 0, 0)
>>> mapdl.k(2, 1, 0, 0)
>>> mapdl.k(3, 1, 1, 0)
>>> mapdl.k(4, 0, 1, 0)
>>> mapdl.l(1, 2)
>>> mapdl.l(2, 3)
>>> mapdl.l(3, 4)
>>> mapdl.l(4, 1)
>>> mapdl.al(1, 2, 3, 4)
```

Open up the gui.

```python
>>> mapdl.open_gui()
```

Resume where you left off.\
继续之前的工作。

```python
>>> mapdl.et(1, 'MESH200', 6)
>>> mapdl.amesh('all')
>>> mapdl.eplot()
```



````