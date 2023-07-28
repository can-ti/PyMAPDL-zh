# Mapdl module

## Mapdl methods and attributes

````{class} ansys.mapdl.core.mapdl._MapdlCore(loglevel='DEBUG', use_vtk=None, log_apdl=None, log_file=False, local=True, print_com=False, **start_parm)

Contains methods in common between all Mapdl subclasses\
包含所有 Mapdl 子类的共同方法


```{table}

| | | |
|---|---|---|
| {doc}`Mapdl.add_file_handler(filepath[, append, level]) <../309_Mapdl_module/Mapdl/add_file_handler>` | Add a file handler to the mapdl log. | 为 mapdl 日志添加文件处理程序。 |
| {doc}`Mapdl.chain_commands <../309_Mapdl_module/Mapdl/chain_commands>` | Chain several mapdl commands. | 连锁多个 mapdl 命令。 |
| {doc}`Mapdl.directory <../309_Mapdl_module/Mapdl/directory>` | Current MAPDL directory. | 当前 MAPDL 目录。 |
| {doc}`Mapdl.get([par, entity, entnum, item1, ...]) <../309_Mapdl_module/Mapdl/get>` | Retrieves a value and stores it as a scalar parameter or part of an array parameter. | 读取数值并将其存储为标量参数或数组参数的一部分。 |
| {doc}`Mapdl.get_array([entity, entnum, item1, ...]) <../309_Mapdl_module/Mapdl/get_array>` | Uses the `*VGET` command to Return an array from ANSYS as a Python array. | 使用 `*VGET` 命令以 Python 数组形式从 ANSYS 返回数组。 |
| {doc}`Mapdl.get_value([entity, entnum, item1, ...]) <../309_Mapdl_module/Mapdl/get_value>` | Runs the MAPDL GET command and returns a Python value. | 运行 MAPDL GET 命令并返回 Python 值。 |
| {doc}`Mapdl.ignore_errors <../309_Mapdl_module/Mapdl/ignore_errors>` | Invalid commands will be ignored rather than exceptions | 无效命令将被忽略，而不是出现异常 |
| {doc}`Mapdl.jobname <../309_Mapdl_module/Mapdl/jobname>` | MAPDL job name. |  |
| {doc}`Mapdl.last_response <../309_Mapdl_module/Mapdl/last_response>` | Returns the last response from MAPDL. | 返回来自 MAPDL 的最后一个响应。 |
| {doc}`Mapdl.load_table(name, array[, var1, var2, ...]) <../309_Mapdl_module/Mapdl/load_table>` | Load a table from Python to into MAPDL. | 将表格从 Python 加载到 MAPDL。 |
| {doc}`Mapdl.mesh <../309_Mapdl_module/Mapdl/mesh>` | Mesh information. | 网格信息。 |
| {doc}`Mapdl.modal_analysis([method, nmode, freqb, ...]) <../309_Mapdl_module/Mapdl/modal_analysis>` | Run a modal with basic settings analysis | 运行带有基本设置分析的模态 |
| {doc}`Mapdl.non_interactive <../309_Mapdl_module/Mapdl/non_interactive>` | Non-interactive context manager. | 非交互式上下文管理器。 |
| {doc}`Mapdl.open_apdl_log(filename[, mode]) <../309_Mapdl_module/Mapdl/open_apdl_log>` | Start writing all APDL commands to an MAPDL input file. | 开始将所有 APDL 命令写入 MAPDL 输入文件。 |
| {doc}`Mapdl.open_gui([include_result, inplace]) <../309_Mapdl_module/Mapdl/open_gui>` | Save the existing database and open it up in the MAPDL GUI. | 保存现有数据库并在 MAPDL GUI 中打开。 |
| {doc}`Mapdl.parameters <../309_Mapdl_module/Mapdl/parameters>` | Collection of MAPDL parameters. | MAPDL 参数集合。 |
| {doc}`Mapdl.run(command[, write_to_log, mute]) <../309_Mapdl_module/Mapdl/run>` | Run single APDL command. |  |
| {doc}`Mapdl.run_multiline(commands) <../309_Mapdl_module/Mapdl/run_multiline>` | Run several commands as a single block. |  |
| {doc}`Mapdl.input_strings(commands) <../309_Mapdl_module/Mapdl/input_strings>` | Run several commands as a single block. |  |
| {doc}`Mapdl.set_log_level(loglevel) <../309_Mapdl_module/Mapdl/set_log_level>` | Sets log level |  |
| {doc}`Mapdl.version <../309_Mapdl_module/Mapdl/version>` | MAPDL build version. |  |

```

````

## Constants

```{table} 
| | | |
|---|---|---|
| {doc}`plotting.ALLOWED_TARGETS <../309_Mapdl_module/Mapdl/ALLOWED_TARGETS>` | Built-in mutable sequence. | 内置的可变序列。 |
| {doc}`plotting.BCS <../309_Mapdl_module/Mapdl/BCS>` | Built-in mutable sequence. | 内置的可变序列。 |

```

## mapdl_grpc.MapdlGrpc methods

````{class} ansys.mapdl.core.mapdl_grpc.MapdlGrpc(ip=None, port=None, timeout=15, loglevel='WARNING', log_file=False, cleanup_on_exit=False, log_apdl=None, set_no_abort=True, remove_temp_files=None, remove_temp_dir_on_exit=False, print_com=False, channel=None, remote_instance=None, **start_parm)

This class connects to a GRPC MAPDL server and allows commands to be passed to a persistent session.\
该类可连接 GRPC MAPDL 服务器，并允许将命令传递给持久会话。

Parameters:
-----------

  *ip* : *`str`* , *`optional`*
  : IP address to connect to the server. The default is 'localhost'.\
  连接服务器的 IP 地址。默认为 'localhost'。

  *port* : *`int`* , *`optional`*
  : Port to connect to the MAPDL server. The default is `50052`.

  *timeout* : *`float`*
  : Maximum allowable time to connect to the MAPDL server.\
  连接 MAPDL 服务器的最长允许时间。

  *logleve* : *`str`* , *`optional`*
  : Sets which messages are printed to the console. Default ‘INFO’ prints out all ANSYS messages, ‘WARNING` prints only messages containing ANSYS warnings, and ‘ERROR’ prints only error messages.

  *cleanup_on_exit* : *`bool`* , *`optional`*
  : Exit MAPDL when Python exits or when this instance is garbage collected.\
  当 Python 退出或此实例被垃圾回收时退出 MAPDL。

  *set_no_abort* : *`bool`* , *`optional`*
  : Sets MAPDL to not abort at the first error within /BATCH mode. The default is `True`.\
  设置 MAPDL 在 /BATCH 模式下第一次出错时不终止。默认为 `True`。

  *remove_temp_dir* : *`bool`* , *`optional`*
  : When this parameter is `True`, the MAPDL working directory will be deleted when MAPDL is exited provided that it is within the temporary user directory. The default is `False`.\
  当该参数为 `True` 时，MAPDL 工作目录将在 MAPDL 退出时被删除，前提是该目录位于临时用户目录内。默认值为 `False`。

  *log_file* : *`bool`* , *`optional`*
  : Copy the log to a file called logs.log located where the python script is executed. The default is `True`.\
  将日志复制到执行 python 脚本所在的名为 logs.log 的文件中。默认值为 `True`。

  *print_com* : *`bool`* , *`optional`*
  : Print the command /COM arguments to the standard output. The default is `False`.

  *channel* : [*`grpc.Channel`*](https://grpc.github.io/grpc/python/grpc.html#grpc.Channel) , *`optional`*
  : gRPC channel to use for the connection. Can be used as an alternative to the `ip` and `port` parameters.\
  连接要使用的 gRPC 通道。可替代 `ip` 和 `port` 参数。

  *remote_instance* : [*`ansys.platform.instancemanagement.Instance`*](https://pypim.docs.pyansys.com/api/_autosummary/ansys.platform.instancemanagement.Instance.html#ansys.platform.instancemanagement.Instance)
  : The corresponding remote instance when MAPDL is launched through PyPIM. This instance will be deleted when calling `Mapdl.exit`.\
  通过 PyPIM 启动 MAPDL 时的相应远程实例。调用 `Mapdl.exit` 时，该实例将被删除。

Examples
-------

Connect to an instance of MAPDL already running on locally on the default port 50052.\
通过默认端口 50052 连接到已在本地运行的 MAPDL 实例。

```python
>>> from ansys.mapdl import core as pymapdl
>>> mapdl = pymapdl.Mapdl()
```

Connect to an instance of MAPDL running on the LAN on a default port.\
通过默认端口连接局域网上运行的 MAPDL 实例。

```python
mapdl = pymapdl.Mapdl('192.168.1.101')
```

Connect to an instance of MAPDL running on the LAN on a non-default port.\
通过非默认端口连接局域网上运行的 MAPDL 实例。

```python
mapdl = pymapdl.Mapdl('192.168.1.101', port=60001)
```

If you wish to customize the channel, you can also directly connect directly to gRPC channels. For example, if you wanted to create an insecure channel with a maximum message length of 8 MB.\
如果希望自定义通道，也可以直接连接到 gRPC 通道。例如，如果您想创建一个最大信息长度为 8 MB 的不安全通道。

```python
import grpc
channel = grpc.insecure_channel(
    '127.0.0.1:50052',
    options=[
        ("grpc.max_receive_message_length", 8*1024**2),
    ],
)
mapdl = pymapdl.Mapdl(channel=channel)
```

```{table}
| | | |
|---|---|---|
| {doc}`mapdl_grpc.MapdlGrpc.download(files[, ...]) <../309_Mapdl_module/mapdl_grpc.MapdlGrpc/download>` | Download files from the gRPC instance working directory | 从 gRPC 实例工作目录下载文件 |
| {doc}`mapdl_grpc.MapdlGrpc.list_error_file() <../309_Mapdl_module/mapdl_grpc.MapdlGrpc/list_error_file>` | Listing of errors written in JOBNAME.err | 写入 JOBNAME.err 的错误列表 |
| {doc}`mapdl_grpc.MapdlGrpc.list_files([refresh_cache]) <../309_Mapdl_module/mapdl_grpc.MapdlGrpc/list_files>` | List the files in the working directory of MAPDL. | 列出 MAPDL 工作目录下的文件。 |
| {doc}`mapdl_grpc.MapdlGrpc.math <../309_Mapdl_module/mapdl_grpc.MapdlGrpc/math>` | APDL math interface |  |
| {doc}`mapdl_grpc.MapdlGrpc.mute <../309_Mapdl_module/mapdl_grpc.MapdlGrpc/mute>` | Silence the response from all MAPDL functions unless explicitly set to `True`. | 静音所有 MAPDL 函数的响应，除非明确设置为 `True`。 |
| {doc}`mapdl_grpc.MapdlGrpc.upload(file_name[, ...]) <../309_Mapdl_module/mapdl_grpc.MapdlGrpc/upload>` | Upload a file to the grpc instance | 向 grpc 实例上传文件 |
```

````

## Information class attribute

```{table}
| | | |
|---|---|---|
| {doc}`Information.product <../309_Mapdl_module/Information/product>` | Retrieve the product from the MAPDL instance. | 从 MAPDL 实例中读取产品。 |
| {doc}`Information.mapdl_version <../309_Mapdl_module/Information/mapdl_version>` | Retrieve the MAPDL version from the MAPDL instance. | 从 MAPDL 实例中读取 MAPDL 版本。 |
| {doc}`Information.pymapdl_version <../309_Mapdl_module/Information/pymapdl_version>` | Retrieve the PyMAPDL version from the MAPDL instance. | 从 MAPDL 实例中读取 PyMAPDL 版本。 |
| {doc}`Information.products <../309_Mapdl_module/Information/products>` | Retrieve the products from the MAPDL instance. | 从 MAPDL 实例中读取产品。 |
| {doc}`Information.preprocessing_capabilities <../309_Mapdl_module/Information/preprocessing_capabilities>` | Retrieve the preprocessing capabilities from the MAPDL instance. | 从 MAPDL 实例读取 preprocessing 功能。 |
| {doc}`Information.aux_capabilities <../309_Mapdl_module/Information/aux_capabilities>` | Retrieve the aux capabilities from the MAPDL instance. | 从 MAPDL 实例读取 aux 功能。 |
| {doc}`Information.solution_options <../309_Mapdl_module/Information/solution_options >` | Retrieve the solution options from the MAPDL instance. | 从 MAPDL 实例中读取 solution 选项。 |
| {doc}`Information.post_capabilities <../309_Mapdl_module/Information/post_capabilities>` | Retrieve the post capabilities from the MAPDL instance. | 从 MAPDL 实例中读取 post 功能。 |
| {doc}`Information.title <../309_Mapdl_module/Information/title>` | Retrieve and set the title from the MAPDL instance. | 从 MAPDL 实例中读取并设置标题。 |
| {doc}`Information.titles <../309_Mapdl_module/Information/titles>` | Retrieve the titles from the MAPDL instance. | 从 MAPDL 实例中读取标题。 |
| {doc}`Information.stitles <../309_Mapdl_module/Information/stitles>` | Retrieve or set the value for the MAPDL stitle (subtitles). | 读取或设置 MAPDL 子标题的值。 |
| {doc}`Information.units <../309_Mapdl_module/Information/units>` | Retrieve the units from the MAPDL instance. | 从 MAPDL 实例中读取单位制。 |
| {doc}`Information.scratch_memory_status <../309_Mapdl_module/Information/scratch_memory_status>` | Retrieve the scratch memory status from the MAPDL instance. | 从 MAPDL 实例读取 scratch memory（暂存内存） 状态。 |
| {doc}`Information.database_status <../309_Mapdl_module/Information/database_status >` | Retrieve the database status from the MAPDL instance. | 从 MAPDL 实例读取数据库状态。 |
| {doc}`Information.config_values <../309_Mapdl_module/Information/config_values>` | Retrieve the config values from the MAPDL instance. | 从 MAPDL 实例中读取配置值。 |
| {doc}`Information.global_status <../309_Mapdl_module/Information/global_status>` | Retrieve the global status from the MAPDL instance. | 从 MAPDL 实例读取全局状态。 |
| {doc}`Information.job_information <../309_Mapdl_module/Information/job_information >` | Retrieve the job information from the MAPDL instance. | 从 MAPDL 实例中读取 job 信息。 |
| {doc}`Information.model_information <../309_Mapdl_module/Information/model_information>` | Retrieve the model information from the MAPDL instance. | 从 MAPDL 实例中读取模型信息。 |
| {doc}`Information.boundary_condition_information <../309_Mapdl_module/Information/boundary_condition_information>` | Retrieve the boundary condition information from the MAPDL instance. | 从 MAPDL 实例中读取边界条件信息。 |
| {doc}`Information.routine_information <../309_Mapdl_module/Information/routine_information>` | Retrieve the routine information from the MAPDL instance. | 从 MAPDL 实例中读取例程信息。 |
| {doc}`Information.solution_options_configuration <../309_Mapdl_module/Information/solution_options_configuration>` | Retrieve the solution options configuration from the MAPDL instance. | 从 MAPDL 实例读取求解选项配置。 |
| {doc}`Information.load_step_options <../309_Mapdl_module/Information/load_step_options>` | Retrieve the load step options from the MAPDL instance. | 从 MAPDL 实例读取荷载步选项。 |
```















