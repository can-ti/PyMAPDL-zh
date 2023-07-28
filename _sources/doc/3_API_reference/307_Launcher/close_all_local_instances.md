# close_all_local_instances

````{function} ansys.mapdl.core.launcher.close_all_local_instances(port_range=None)

Close all MAPDL instances within a port_range.\
关闭端口范围内的所有 MAPDL 实例。

This function can be used when cleaning up from a failed pool or batch run.\
该功能可用于清理失败的池或批处理运行。

Parameters：
-----------

  *port_range* : *`list`* , *`optional`*
  : Defaults to `range(50000, 50200)`. Expand this range if there are many potential instances of MAPDL in gRPC mode.\
  默认为 `range(50000,50200)`。如果在 gRPC 模式下有许多潜在的 MAPDL 实例，请扩大此范围。

Examples
--------

Close all instances on in the range of 50000 and 50199.

```python
>>> import ansys.mapdl.core as pymapdl
>>> pymapdl.close_all_local_instances()
```

````