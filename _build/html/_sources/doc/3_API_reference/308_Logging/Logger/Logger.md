# Logger

````{class} ansys.mapdl.core.logging.Logger(level=10, to_file=False, to_stdout=True, filename='pymapdl.log')

Logger used for each Pymapdl session.\
每个 Pymapdl 会话使用的日志记录器。

This class allows you to add handlers to the logger to output to a file or standard output.\
通过该类，您可以向日志记录器添加处理程序，以输出到文件或标准输出。

Parameters:
---------

  *level* : *`int`* , *`optional`*
  : Logging level to filter the message severity allowed in the logger. The default is `logging.DEBUG`.\
  日志级别，用于过滤日志记录器中允许的消息严重性。默认为 `logging.DEBUG`。

  *to_file* : *`bool`* , *`optional`*
  : Write log messages to a file. The default is `False`.

  *to_stdout* : *`bool`* , *`optional`*
  : Write log messages into the standard output. The default is `True`.\
  将日志信息写入标准输出。默认为 `True`。

  *filename* : *`str`* , *`optional`*
  : Name of the file where log messages are written to. The default is `None`.\
  写入日志信息的文件名。默认为 `None`。

Examples
------------

Demonstrate logger usage from an instance mapdl. This is automatically created when creating an Mapdl instance.\
从实例 mapdl 演示日志记录器的使用。创建 Mapdl 实例时会自动创建该日志。

```python

>>> from ansys.mapdl.core import launch_mapdl
>>> mapdl = launch_mapdl(loglevel='DEBUG')
>>> mapdl._log.info('This is a useful message')
INFO -  -  <ipython-input-24-80df150fe31f> - <module> - This is LOG debug message

```

Import the global pymapdl logger and add a file output handler.\
导入全局 pymapdl 日志记录器并添加文件输出处理程序。

```python

>>> import os
>>> from ansys.mapdl.core import LOG
>>> file_path = os.path.join(os.getcwd(), 'pymapdl.log')
>>> LOG.log_to_file(file_path)

```

Methods
-------

```{table}

| | | |
|---|---|---|
| {doc}`Logger.add_child_logger(sufix[, level])  <../Logger/add_child_logger>` | Add a child logger to the main logger. | 为主日志记录器添加子日志记录器。 |
| {doc}`Logger.add_handling_uncaught_expections(logger) <../Logger/add_handling_uncaught_expections>` | This just redirect the output of an exception to the logger. | 这只是将异常输出重定向到日志记录器。 |
| {doc}`Logger.add_instance_logger(name, mapdl_instance) <../Logger/add_instance_logger>` | Create a logger for a MAPDL instance. | 为 MAPDL 实例创建日志记录器。 |
| {doc}`Logger.log_to_file([filename, level]) <../Logger/log_to_file>` | Add file handler to logger. | 为日志程序添加文件处理程序。 |
| {doc}`Logger.log_to_stdout([level]) <../Logger/log_to_stdout>` | Add standard output handler to the logger. | 为日志程序添加标准输出处理程序。 |
| {doc}`Logger.setLevel([level]) <../Logger/setLevel>` | Change the log level of the object and the attached handlers. | 更改对象和所附处理程序的日志级别。 |

```

Attributes
----------

```{table}

| | | |
|---|---|---|
| {doc}`Logger.file_handler <../Logger/file_handler>` |  |  |
| {doc}`Logger.std_out_handler <../Logger/std_out_handler>` |  |  |

```

````