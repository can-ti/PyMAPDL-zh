# non_interactive

````{property} property Mapdl.non_interactive

Non-interactive context manager.\
非交互式上下文管理器。

Allow to execute code without user interaction or waiting between PyMAPDL responses. It can also be used to execute some commands which are not supported in interactive mode. For a complete list of commands visit [Unsupported “interactive” commands](https://mapdl.docs.pyansys.com/version/stable/user_guide/mapdl.html#ref-unsupported-interactive-commands).\
允许在 PyMAPDL 响应之间执行代码，无需用户交互或等待。它还可以用来执行一些在交互模式下不支持的命令。有关命令的完整列表，请访问 {doc}`Unsupported “interactive” commands <../1_User_guide/102_PyMAPDL语法和用法>` 。

View the last response with {doc}`Mapdl.last_response <../Mapdl.last_response>` method.\
使用 {doc}`Mapdl.last_response <../Mapdl.last_response>` 方法查看最后一次响应。

Notes
------

All the commands executed inside this context manager are not executed until the context manager exits which then execute them all at once in the MAPDL instance.\
在该上下文管理器中执行的所有命令都不会被执行，直到上下文管理器退出，然后在 MAPDL 实例中一次性执行所有命令。

This command uses `Mapdl.input()` method.


Examples
---------

Use the non-interactive context manager for the VWRITE ( `Mapdl.vwrite()`) command.\
为 VWRITE（"Mapdl.vwrite()"）命令使用非交互式上下文管理器。

```python
>>>with mapdl.non_interactive:
   mapdl.run("*VWRITE,LABEL(1),VALUE(1,1),VALUE(1,2),VALUE(1,3)")
   mapdl.run("(1X,A8,'   ',F10.1,'  ',F10.1,'   ',1F5.3)")
>>> mapdl.last_response
```



````