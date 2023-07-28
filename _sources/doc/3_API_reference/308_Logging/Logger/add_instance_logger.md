# add_instance_logger

```{method} Logger.add_instance_logger(name, mapdl_instance, level=None)

Create a logger for a MAPDL instance.\
为 MAPDL 实例创建日志记录器。

The MAPDL instance logger is a logger with an adapter which add the contextual information such as MAPDL instance name. This logger is returned and you can use it to log events as a normal logger. It is also stored in the `_instances` field.\
MAPDL 实例日志记录器是一种带有适配器的日志记录器，可添加上下文信息（如 MAPDL 实例名称）。此日志记录器会返回，您可以像使用普通日志记录器一样使用它来记录事件。它也存储在 `_instances` 字段中。

Parameters:
--------

  *name* : *`str`*
  : Name for the new logger

  *mapdl_instance* : [`https://mapdl.docs.pyansys.com/version/stable/api/mapdl.html#ansys.mapdl.core.mapdl._MapdlCore`](https://mapdl.docs.pyansys.com/version/stable/api/mapdl.html#ansys.mapdl.core.mapdl._MapdlCore)
  : Mapdl instance object. This should contain the attribute `name`.\
  Mapdl 实例对象。该对象应包含属性 `name`。


Returns:
---------

  `ansys.mapdl.core.logging.PymapdlCustomAdapter`
  : Logger adapter customized to add MAPDL information to the logs. You can use this class to log events in the same way you would with the logger class.\
  日志记录器适配器是为在日志中添加 MAPDL 信息而定制的。您可以使用该类来记录事件，方法与使用日志记录器类相同。

Raises:
--------

  `Exception`
  : You can only input strings as name to this method.\
  该方法只能输入字符串作为名称。




```