# chain_commands

````{property} Mapdl.chain_commands

Chain several mapdl commands.\
链接多个 mapdl 命令。

Commands can be separated with `"$"` in MAPDL rather than with a line break, so you could send multiple commands to MAPDL with:\
在 MAPDL 中，命令可以用"$"分隔，而不用换行，因此您可以向 MAPDL 发送多条命令：

`mapdl.run("/PREP7$K,1,1,2,3")`

This method is merely a convenience context manager to allow for easy chaining of PyMAPDL commands to speed up sending commands to MAPDL.\
该方法只是一个方便的上下文管理器，可以方便地链上 PyMAPDL 命令，加快向 MAPDL 发送命令的速度。

View the response from MAPDL with {doc}`Mapdl.last_response <../309_Mapdl_module/Mapdl/last_response>`.\
使用 `Mapdl.last_response` 查看 MAPDL 的响应。

Notes
------

Distributed Ansys cannot properly handle condensed data input and chained commands are not permitted in distributed ansys.\
分布式 Ansys 无法正确处理压缩数据输入，而且分布式 Ansys 中不允许使用链式命令。

Examples
---------

```python
>>> with mapdl.chain_commands:
    mapdl.prep7()
    mapdl.k(1, 1, 2, 3)
```

````