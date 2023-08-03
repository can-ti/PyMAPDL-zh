# run

````{method} Mapdl.run(command, write_to_log=True, mute=None, **kwargs)

Run single APDL command.\
运行单条 APDL 命令。

For multiple commands, use {doc}`Mapdl.input_strings() <../Mapdl.input_strings>`.\
对于多条命令，请使用 {doc}`Mapdl.input_strings() <../Mapdl.input_strings>`.

Parameters:
----------

  command : *`str`*
  : ANSYS APDL command.

  write_to_log : *`bool`* , *`optional`*
  : Overrides APDL log writing. Default `True`. When set to `False`, will not write command to log, even if APDL command logging is enabled.\
  覆盖 APDL 日志写入。默认为 `True`。设置为 `False` 时，即使启用了 APDL 命令记录，也不会将命令写入日志。

  kwargs : *`dict`* , *`optional`*
  : These keyword arguments are interface specific or for development purposes.

    avoid_non_interactivebool : *`bool`*
    : *(Development use only)* Avoids the non-interactive mode for this specific command. Defaults to `False`.\
    *（仅用于开发）* 避免此特定命令的非交互模式。默认为 `False`。

    verbose : *`bool`*
    : Prints the command to the screen before running it. Defaults to `False`.\
    在运行命令前将其打印到屏幕上。默认为 `False`。

Returns:
--------

  `str`
  : 
Command output from MAPDL.

Notes
--------

Running non-interactive commands

When two or more commands need to be run non-interactively (i.e. `*VWRITE`) use\
当需要非交互运行两条或更多命令时（如`*VWRITE`），使用

```python
>>> with mapdl.non_interactive:
    mapdl.run("*VWRITE,LABEL(1),VALUE(1,1),VALUE(1,2),VALUE(1,3)")
    mapdl.run("(1X,A8,'   ',F10.1,'  ',F10.1,'   ',1F5.3)")
```

Alternatively, you can simply run a block of commands with:\
或者，您也可以使用以下命令运行一个命令块：

```python
>>> mapdl.input_strings(cmd)
```

Examples
----------

```python
>>> mapdl.run('/PREP7')
```

Equivalent Pythonic method:

```python
>>> mapdl.prep7()
```


````