# convert_apdl_block

````{method} ansys.mapdl.core.convert.convert_apdl_block(apdl_strings, loglevel='WARNING', auto_exit=True, line_ending=None, exec_file=None, macros_as_functions=True, use_function_names=True, show_log=False, add_imports=True, comment_solve=False, cleanup_output=True, header=True, print_com=True, only_commands=False)

Converts an ANSYS input string to a python PyMAPDL string.\
将 ANSYS 输入字符串转换为 python PyMAPDL 字符串。

Parameters:
-----------

  *apdl_string* : *`str`*
  : APDL strings or list of strings to convert.\
  要转换的 APDL 字符串或字符串列表。

  *loglevel* : *`str`* , *`optional`*
  : Logging level of the ansys object within the script.\
  脚本中 ansys 对象的日志级别。

  *auto_exit* : *`bool`* , *`optional`*
  : Adds a line to the end of the script to exit MAPDL. Default `True`.
  在脚本末尾添加一行以退出 MAPDL。默认为 `True`。

  *line_ending* : *`str`* , *`optional`*
  : When `None`, automatically determined by OS being used.\
  当为 `None` 时，由所使用的操作系统自动决定。

  *macros_as_functions* : *`bool`* , *`optional`*
  : Attempt to convert MAPDL macros to python functions.\
  尝试将 MAPDL 宏转换为 python 函数。

  *use_function_names* : *`bool`* , *`optional`*
  : Convert MAPDL functions to ansys.mapdl.core.Mapdl class methods. When `True`, the MAPDL command “K” will be converted to `mapdl.k`. When `False`, it will be converted to `mapdl.run('k')`.\
  将 MAPDL 函数转换为 ansys.mapdl.core.Mapdl 类方法。当为 `True` 时，MAPDL 命令 `K` 将转换为 `mapdl.k`。为 `False` 时，将转换为 `mapdl.run('k')`。

  *show_log* : *`bool`* , *`optional`*
  : Print the converted commands using a logger (from `logging` Python module).\
  使用日志程序（来自 `logging` Python 模块）打印转换后的命令。

  *add_imports* : *`bool`* , *`optional`*
  : If `True`, add the lines `from ansys.mapdl.core import launch_mapdl` and `mapdl = launch_mapdl(loglevel="WARNING")` to the beginning of the output file. This option is useful if you are planning to use the output script from another mapdl session. See examples section. This option overrides `auto_exit`.\
  如果 `true`，则在输出文件的开头添加 `from ansys.mapdl.core import launch_mapdl` 和 `mapdl = launch_mapdl(loglevel="WARNING")`。如果你计划使用另一个 mapdl 会话的输出脚本，该选项会非常有用。参见示例部分。此选项覆盖 `auto_exit`。

  *comment_solve* ： *`bool`* , *`optional`*
  : If `True`, pythonically comment the lines containing `mapdl.solve` or `"/EOF"`.\
  如果 `True`，则对包含 `mapdl.solve` 或 `"/EOF"` 的行以 python 的方式注释。

  *cleanup_output* : *`bool`* , *`optional`*
  : If `True` the output is formatted using `autopep8` before writing the file or returning the string.\
  如果为 `True`，则在写入文件或返回字符串之前使用 `autopep8` 对输出进行格式化。

  *header* : *`bool`* , *`optional`*
  : If `True`, the default header is written in the first line of the output. If a string is provided, this string will be used as header.\
  如果为 `True`，则在输出的第一行写入默认标头。如果提供的是字符串，该字符串将被用作标头。

  *print_com* ： *`bool`* , *`optional`*
  ： Print command `/COM` arguments to python console. Defaults to `True`.\
  将命令 `/COM` 参数打印到 python 控制台。默认值为 `True` 。

  *only_commands* : *`bool`* , *`optional`*
  : If `True`, it converts only the commands, meaning that header (`header=False`), imports (`add_imports=False`), and exit commands are NOT included (`auto_exit=False`). Overrides `header`, `add_imports` and `auto_exit`.\
  如果为 `True`，则只转换命令，这意味着不包括 header (`header=False`)、imports (`add_import=False`)和退出命令 (`auto_exit=False`)。覆盖 `header`、`add_import` 和 `auto_exit`。

Returns:
---------

  `list`
  : List of lines translated.

Examples
---------

Convert a script and use it in the same session.\
转换脚本并在同一会话中使用。

```python
>>> from ansys.mapdl.core import examples, launch_mapdl, convert_apdl_block
>>> in_file = examples.vmfiles['vm10']
>>> filename = in_file.split('\')[-1]
>>> out_file = 'out_' + filename.replace('.dat', '.py')
>>> cmds = convert_apdl_block(file, out_file, line_ending='\n')
>>> # Do any change in the text, for example:
>>> cmds = cmds.replace('solve', '!solve')
>>> mapdl = launch_mapdl()
>>> mapdl.input_strings(cmds.splitlines()[2:10])
```


````