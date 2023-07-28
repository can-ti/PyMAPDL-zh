# add_child_logger

```{method} Logger.add_child_logger(sufix, level=None)

Add a child logger to the main logger.\
为主日志记录器添加子日志记录器。

This logger is more general than an instance logger which is designed to track the state of the MAPDL instances.\
该日志记录器比实例日志记录器更通用，后者旨在跟踪 MAPDL 实例的状态。

If the logging level is in the arguments, a new logger with a reference to the `_global` logger handlers is created instead of a child.\
如果参数中包含日志记录级别，则会创建一个引用了 `_global`日志记录器处理程序的新日志记录器，而不是子日志记录器。

Parameters:
------------

  *sufix* : *`str`*
  : Name of the logger.

  *level* : *str* , *`optional`*
  : Level of logging

Returns:
----------

  `logging.logger`
  : Logger class.



```