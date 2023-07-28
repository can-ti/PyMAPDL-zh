# convert_script

````{method} ansys.mapdl.core.convert.convert_script(filename_in, filename_out=None,loglevel='WARNING', auto_exit=True, line_ending=None, exec_file=None, macros_as_functions=True, use_function_names=True, show_log=False, add_imports=True, comment_solve=False, cleanup_output=True, header=True, print_com=True, only_commands=False)

Converts an ANSYS input file to a python PyMAPDL script.\
将 ANSYS 输入文件转换为 python PyMAPDL 脚本。。

Parameters:
-----------

  *filename_in* : *`str`*
  : Filename of the ansys input file to read in.\
  要读入的 ansys 输入文件的文件名。

   *filename_out* : *`str`*, *`optional`*
  : Filename of the python script to write a translation to.Defaults to the `filename_in` name ending in `py`.\
  要写入的 python 脚本的文件名。默认为以 `py` 结尾的 `filename_in` 名称。

  *loglevel* : *`str`* , *`optional`*
  : Logging level of the ansys object within the script.\
  脚本中 ansys 对象的日志级别。

  *auto_exit* : *`bool`* , *`optional`*
  : Adds a line to the end of the script to exit MAPDL. Default `True`.
  在脚本末尾添加一行以退出 MAPDL。默认为 `True`。

  *line_ending* : *`str`* , *`optional`*
  : When `None`, automatically is `\n.`\
  当 `None` 时，自动为 `\n.`。

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

```python
>>> from ansys.mapdl import core as pymapdl
>>> from ansys.mapdl.core import examples
>>> clines = pymapdl.convert_script(examples.vmfiles['vm1'], 'vm1.py')
```

Converting a script and using it already in the same session. For this case, it is recommended to use `convert_apdl_block()` since you do not need to write the file.\
转换脚本并已在同一会话中使用。在这种情况下，建议使用 `convert_apdl_block()`，因为您不需要再写入文件。

```python
# 导入所需的模块和函数
import os
from ansys.mapdl.core import launch_mapdl
from ansys.mapdl.core import examples
from ansys.mapdl.core import convert_script

# 获取示例输入文件的路径和文件名，并构造输出文件名，将 '.dat' 替换为 '.py'
in_file = examples.vmfiles['vm10']
filename = os.path.basename(in_file)
out_file = 'out_' + filename.replace('.dat', '.py')

# 将输入的 APDL 脚本转换成 Python 脚本，并保存在输出文件中
output = convert_script(in_file, out_file, line_ending='\n')

# 启动 ANSYS Mechanical APDL 进程，允许通过 Python 与其交互
mapdl = launch_mapdl()

# 打开输出的 Python 脚本文件并读取其中的内容
with open(out_file, 'r') as fid:
    cmds = fid.read()

# 将 Python 脚本的第 2 行到第 9 行（不包括第 10 行）作为 ANSYS APDL 命令输入到 MAPDL 会话中执行
mapdl.input_strings(cmds.splitlines()[2:10])

```

````