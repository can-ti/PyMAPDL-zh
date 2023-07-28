# Mapdl methods and attributes

````{class} ansys.mapdl.core.mapdl._MapdlCore(loglevel='DEBUG', use_vtk=None, log_apdl=None, log_file=False, local=True, print_com=False, **start_parm)

Contains methods in common between all Mapdl subclasses\
包含所有 Mapdl 子类的共同方法


```{table}

| | | |
|---|---|---|
| {doc}`Mapdl.add_file_handler(filepath[, append, level]) <../Mapdl/add_file_handler>` | Add a file handler to the mapdl log. | 为 mapdl 日志添加文件处理程序。 |
| {doc}`Mapdl.chain_commands <../Mapdl/chain_commands>` | Chain several mapdl commands. | 连锁多个 mapdl 命令。 |
| {doc}`Mapdl.directory <../Mapdl/directory>` | Current MAPDL directory. | 当前 MAPDL 目录。 |
| {doc}`Mapdl.get([par, entity, entnum, item1, ...]) <../Mapdl/get>` | Retrieves a value and stores it as a scalar parameter or part of an array parameter. | 读取数值并将其存储为标量参数或数组参数的一部分。 |
| {doc}`Mapdl.get_array([entity, entnum, item1, ...]) <../Mapdl/get_array>` | Uses the `*VGET` command to Return an array from ANSYS as a Python array. | 使用 `*VGET` 命令以 Python 数组形式从 ANSYS 返回数组。 |
| {doc}`Mapdl.get_value([entity, entnum, item1, ...]) <../Mapdl/get_value>` | Runs the MAPDL GET command and returns a Python value. | 运行 MAPDL GET 命令并返回 Python 值。 |
| {doc}`Mapdl.ignore_errors <../Mapdl/ignore_errors>` | Invalid commands will be ignored rather than exceptions | 无效命令将被忽略，而不是出现异常 |
| {doc}`Mapdl.jobname <../Mapdl/jobname>` | MAPDL job name. |  |
| {doc}`Mapdl.last_response <../Mapdl/last_response>` | Returns the last response from MAPDL. | 返回来自 MAPDL 的最后一个响应。 |
| {doc}`Mapdl.load_table(name, array[, var1, var2, ...]) <../Mapdl/load_table>` | Load a table from Python to into MAPDL. | 将表格从 Python 加载到 MAPDL。 |
| {doc}`Mapdl.mesh <../Mapdl/mesh>` | Mesh information. | 网格信息。 |
| {doc}`Mapdl.modal_analysis([method, nmode, freqb, ...]) <../Mapdl/modal_analysis>` | Run a modal with basic settings analysis | 运行带有基本设置分析的模态 |
| {doc}`Mapdl.non_interactive <../Mapdl/non_interactive>` | Non-interactive context manager. | 非交互式上下文管理器。 |
| {doc}`Mapdl.open_apdl_log(filename[, mode]) <../Mapdl/open_apdl_log>` | Start writing all APDL commands to an MAPDL input file. | 开始将所有 APDL 命令写入 MAPDL 输入文件。 |
| {doc}`Mapdl.open_gui([include_result, inplace]) <../Mapdl/open_gui>` | Save the existing database and open it up in the MAPDL GUI. | 保存现有数据库并在 MAPDL GUI 中打开。 |
| {doc}`Mapdl.parameters <../Mapdl/parameters>` | Collection of MAPDL parameters. | MAPDL 参数集合。 |
| {doc}`Mapdl.run(command[, write_to_log, mute]) <../Mapdl/run>` | Run single APDL command. |  |
| {doc}`Mapdl.run_multiline(commands) <../Mapdl/run_multiline>` | Run several commands as a single block. |  |
| {doc}`Mapdl.input_strings(commands) <../Mapdl/input_strings>` | Run several commands as a single block. |  |
| {doc}`Mapdl.set_log_level(loglevel) <../Mapdl/set_log_level>` | Sets log level |  |
| {doc}`Mapdl.version <../Mapdl/version>` | MAPDL build version. |  |

```

````

## Constants

```{table} 
| | | |
|---|---|---|
| {doc}`plotting.ALLOWED_TARGETS <../Mapdl/ALLOWED_TARGETS>` | Built-in mutable sequence. | 内置的可变序列。 |
| {doc}`plotting.BCS <../Mapdl/BCS>` | Built-in mutable sequence. | 内置的可变序列。 |

```