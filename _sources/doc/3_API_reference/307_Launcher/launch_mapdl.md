# launch_mapdl

`````{function} ansys.mapdl.core.launcher.launch_mapdl(exec_file=None, run_location=None, jobname='file', nproc=2, ram=None, mode=None, override=False, loglevel='ERROR', additional_switches='', start_timeout=45, port=None, cleanup_on_exit=True, start_instance=None, ip=None, clear_on_connect=True, log_apdl=None, remove_temp_files=None, remove_temp_dir_on_exit=False, verbose_mapdl=None, license_server_check=True, license_type=None, print_com=False, add_env_vars=None, replace_env_vars=None, version=None, **kwargs)

Start MAPDL locally.

Parameters:
-----------

  *exec_file* : *`str`* , *`optional`*
  : The location of the MAPDL executable. Will use the cached location when left at the default `None` and no environment variable is set.\
  MAPDL 可执行文件的位置。默认为 "无 "且未设置环境变量时，将使用缓存位置。
  ````{note}
  The executable path can be also set through the environment variable PYMAPDL_MAPDL_EXEC. For example:\
  也可通过环境变量 PYMAPDL_MAPDL_EXEC 设置可执行路径。例如
  ```
  export PYMAPDL_MAPDL_EXEC=/ansys_inc/v211/ansys/bin/mapdl
  ```
  ````

  *run_location* : *`str`* , *`optional`*
  : MAPDL working directory. Defaults to a temporary working directory. If directory doesn’t exist, one is created.\
  MAPDL 工作目录。默认为临时工作目录。如果目录不存在，则会创建一个。

  *jobname* : *`str`* , *`optional`*
  : MAPDL jobname. Defaults to `'file'`.

  *nproc* : *`int`* , *`optional`*
  : Number of processors. Defaults to 2.\
  处理器数量。默认为 2。

  *ram* : *`float`* , *`optional`*
  : Fixed amount of memory to request for MAPDL. If `None`, then MAPDL will use as much as available on the host machine.\
  为 MAPDL 申请的固定内存量。如果 "无"，则 MAPDL 将使用主机上的可用内存。

  *mode* : *`str`* , *`optional`*
  : Mode to launch MAPDL. Must be one of the following:\
  启动 MAPDL 的模式。必须是以下之一:\
  - `'grpc'` - `'grpc'` 模式在 ANSYS 2021R1 或更新版本上可用，具有最佳性能和稳定性。
  - `'corba'` - `'corba'` 模式从 v17.0 及更新版本起可用，并获得传统支持。该模式需要额外的 ansys_corba 模块。
  - `'console'` - `'comsole'` 模式仅适用于 v17.0 之前的 Linux。此控制台模式待折旧。有关详细信息，请访问[版本和接口](https://mapdl.docs.pyansys.com/version/stable/getting_started/versioning.html#versions-and-interfaces)。

  *override* : *`bool`* , *`optional`*
  : Attempts to delete the lock file at the `run_location`. Useful when a prior MAPDL session has exited prematurely and the lock file has not been deleted.\
  尝试删除 `run_location` 中的锁定文件。当先前的 MAPDL 会话过早退出，而锁定文件尚未删除时，此功能非常有用。

  *loglevel* : *`str`* , *`optional`*
  : Sets which messages are printed to the console. `'INFO'` prints out all ANSYS messages, `'WARNING'` prints only messages containing ANSYS warnings, and `'ERROR'` logs only error messages.\
  设置将哪些信息打印到控制台。`'INFO'`打印所有 ANSYS 信息，`'WARNING'`只打印包含 ANSYS 警告的信息，`'ERROR'`只记录错误信息。

  *additional_switches* : *`str`* , *`optional`*
  : Additional switches for MAPDL, for example 'aa_r', the academic research license, would be added with:\
  MAPDL 的附加开关，例如 `'aa_r'`，即学术研究许可证，可通过以下方式添加：\
  - `additional_switches="-aa_r"`
  Avoid adding switches like `-i`, `-o` or `-b` as these are already included to start up the MAPDL server. See the notes section for additional details.\
  避免添加 `-i`、`-o` 或 `-b` 等开关，因为启动 MAPDL 服务器时已包含这些开关。有关更多详情，请参阅注释部分。

  *start_timeout* : *`float`*, *`optional`*
  : Maximum allowable time to connect to the MAPDL server.\
  连接 MAPDL 服务器的最长允许时间。

  *port* : *`int`*
  : Port to launch MAPDL gRPC on. Final port will be the first port available after (or including) this port. Defaults to 50052. You can also override the port default with the environment variable `PYMAPDL_PORT=<VALID PORT>` This argument has priority over the environment variable.\
  启动 MAPDL gRPC 的端口。最终端口将是该端口之后（或包括该端口）的第一个可用端口。默认为 50052。您也可以使用环境变量 `PYMAPDL_PORT=<VALID PORT>` 来覆盖默认端口，该参数的优先级高于环境变量。

  *custom_bin* : *`str`* , *`optional`*
  : Path to the MAPDL custom executable. On release 2020R2 on Linux, if `None`, will check to see if you have `ansys.mapdl_bin` installed and use that executable.\
  MAPDL 自定义可执行文件的路径。在 Linux 上的 2020R2 版中，如果 `None`，将检查是否安装了 `ansys.mapdl_bin` 并使用该可执行文件。

  *cleanup_on_exit* : *`bool`* , *`optional`*
  : Exit MAPDL when python exits or the mapdl Python instance is garbage collected.\
  当 python 退出或 mapdl Python 实例被垃圾回收时，退出 MAPDL。

  *start_instance* : *`bool`* , *`optional`*
  : When `False`, connect to an existing MAPDL instance at `ip` and `port`, which default to ip `'127.0.0.1'` at port **50052**. Otherwise, launch a local instance of MAPDL. You can also override the default behavior of this keyword argument with the environment variable `PYMAPDL_START_INSTANCE=FALSE`.\
  当为 `False` 时，将连接到位于 `ip` 和 `port` 的现有 MAPDL 实例，默认端口为 ip `'127.0.0.1'` 和端口 **50052**。否则，启动一个本地 MAPDL 实例。您也可以使用环境变量 `PYMAPDL_START_INSTANCE=FALSE` 来覆盖此关键字参数的默认行为。

  *ip* : *`bool`* , *`optional`*
  : Used only when `start_instance` is `False`. If provided, it will force `start_instance` to be `False`. Specify the IP address of the MAPDL instance to connect to. You can also provide a hostname as an alternative to an IP address. Defaults to `'127.0.0.1'`. You can also override the default behavior of this keyword argument with the environment variable `PYMAPDL_IP=<IP>`. This argument has priority over the environment variable.\
  仅在 `start_instance` 为 `False` 时使用。如果提供，将强制 `start_instance` 为 `False`。指定要连接的 MAPDL 实例的 IP 地址。也可以提供主机名作为 IP 地址的替代。默认为 `'127.0.0.1'`。您也可以使用环境变量 `PYMAPDL_IP=<IP>` 来覆盖此关键字参数的默认行为。该参数的优先级高于环境变量。

  *clear_on_connect* : *`bool`* , *`optional`*
  : Defaults to `True`, giving you a fresh environment when connecting to MAPDL. When if `start_instance` is specified it defaults to `False`.\
  默认为 `True`，以便在连接到 MAPDL 时为您提供一个全新的环境。如果指定了 `start_instance`，则默认为 `False`。

  *log_apdl* : *`str`* , *`optional`*
  : Enables logging every APDL command to the local disk. This can be used to “record” all the commands that are sent to MAPDL via PyMAPDL so a script can be run within MAPDL without PyMAPDL. This argument is the path of the output file (e.g. `log_apdl='pymapdl_log.txt'`). By default this is disabled.\
  启用将每一条 APDL 命令记录到本地磁盘。这可以用来 "记录 "所有通过 PyMAPDL 发送到 MAPDL 的命令，这样就可以在 MAPDL 中运行脚本，而不需要 PyMAPDL。这个参数是输出文件的路径 (例如 `log_apdl='pymapdl_log.txt'`).默认禁用。

  *remove_temp_files* : *`bool`* , *`optional`*
  : 
  ```{warning} 
  ***Deprecated since version 0.64.0:*** Use argument `remove_temp_dir_on_exit` instead.\
  自 0.64.0 版起已被弃用：使用参数 `remove_temp_dir_on_exit` 代替。
  ```
  When `run_location` is `None`, this launcher creates a new MAPDL working directory within the user temporary directory, obtainable with `tempfile.gettempdir()`. When this parameter is `True`, this directory will be deleted when MAPDL is exited. Default `False`.\
  当 `run_location` 为 `None` 时，启动器将在用户临时目录中创建一个新的 MAPDL 工作目录，该目录可通过 `tempfile.gettempdir()` 获取。如果此参数为 `True`，则在退出 MAPDL 时删除此目录。默认为 `False`。

  *remove_temp_dir_on_exit* : *`bool`* , *`optional`*
  : When `run_location` is `None`, this launcher creates a new MAPDL working directory within the user temporary directory, obtainable with `tempfile.gettempdir()`. When this parameter is `True`, this directory will be deleted when MAPDL is exited. Default `False`. If you change the working directory, PyMAPDL does not delete the original working directory nor the new one.\
  当 `run_location` 为 `None` 时，启动器将在用户临时目录中创建一个新的 MAPDL 工作目录，该目录可通过 `tempfile.gettempdir()` 获得。如果此参数为 `True`，则在退出 MAPDL 时删除此目录。默认为`False`。如果更改了工作目录，PyMAPDL 不会删除原来的工作目录，也不会删除新的工作目录。

  *verbose_mapdl* : *`bool`* , *`optional`*
  : Enable printing of all output when launching and running MAPDL. This should be used for debugging only as output can be tracked within pymapdl. Default `False`.\
  启动和运行 MAPDL 时，启用打印所有输出。这只能用于调试，因为输出可以在 pymapdl 中跟踪。默认为 `False`。
  ```{warning}
  ***Deprecated since version v0.65.0:*** The `verbose_mapdl` argument is deprecated and will be removed in a future release. Use a [logger](https://mapdl.docs.pyansys.com/version/stable/api/logging.html#api-logging) instead. See Logging for more details.\
  ***自 v0.65.0 版起已被弃用：*** `verbose_mapdl` 参数已被弃用，并将在未来版本中删除。请使用日志记录器代替。更多详情，请参阅[日志记录](https://mapdl.docs.pyansys.com/version/stable/api/logging.html#api-logging)。
  ```

  *license_server_check* : *`bool`* , *`optional`*
  : Check if the license server is available if MAPDL fails to start. Only available on `mode='grpc'`. Defaults `True`.\
  : 如果 MAPDL 启动失败，检查许可证服务器是否可用。仅适用于 `mode='grpc'`。默认为 `True`。

  *license_type* : *`str`* , *`optional`*
  : Enable license type selection. You can input a string for its license name (for example `'meba'` or `'ansys'`) or its description (“enterprise solver” or “enterprise” respectively). You can also use legacy licenses (for example `'aa_t_a'`) but it will also raise a warning. If it is not used (`None`), no specific license will be requested, being up to the license server to provide a specific license type. Default is `None`.\
  启用许可证类型选择。可以输入一个字符串作为许可证名称（例如 "meba "或 "ansys"）或描述（分别为 "企业求解器 "或 "企业"）。也可以使用传统许可证（例如 `'aa_t_a'`），但也会引发警告。如果不使用 (`None`)，则不会请求特定的许可证，而是由许可证服务器提供特定的许可证类型。默认为 `None`。

  *print_com* : *`bool`* , *`optional`*
  : Print the command `/COM` arguments to the standard output. Default `False`.\
  将命令 `/COM` 参数打印到标准输出。默认为 `False`。

  *add_env_vars* : *`dict`* , *`optional`*
  : The provided dictionary will be used to extend the system or process environment variables. If you want to control all of the environment variables, use `replace_env_vars`. Defaults to `None`.\
  所提供的字典将用于扩展系统或进程的环境变量。如果要控制所有环境变量，请使用 `replace_env_vars`。默认值为 `None`。

  *replace_env_vars* : *`dict`* , *`optional`*
  : The provided dictionary will be used to replace all the system or process environment variables. To just add some environment variables to the MAPDL process, use `add_env_vars`. Defaults to `None`.\
  所提供的字典将用于替换所有系统或进程环境变量。如果只想在 MAPDL 进程中添加一些环境变量，请使用 `add_env_vars`。默认值为 `None`。

  *version* : *`float`* , *`optional`*
  : Version of MAPDL to launch. If None, the latest version is used. Versions can be provided as integers (i.e. `version=222`) or floats (i.e. `version=22.2`). To retrieve the available installed versions, use the function `ansys.tools.path.path.get_available_ansys_installations()`.\
  要启动的 MAPDL 版本。如果无，则使用最新版本。版本可以整数（如 `version=222`）或浮点数（如 `version=22.2`）形式提供。要检索可用的已安装版本，请使用函数 `ansys.tools.path.path.get_available_ansys_installations()`。
  ````{note}
  The default version can be also set through the environment variable `PYMAPDL_MAPDL_VERSION`. For example:\
  默认版本也可通过环境变量 `PYMAPDL_MAPDL_VERSION` 设置。例如
  ```
  export PYMAPDL_MAPDL_VERSION=22.2
  ```
  ````

  *kwargs* : *`dict`* , *`optional`*
  : These keyword arguments are interface specific or for development purposes. See Notes for more details.\
  这些关键字参数针对特定界面或用于开发目的。详情请参阅注释。

    *set_no_abort* : *`bool`*
    : *(Development use only)* Sets MAPDL to not abort at the first error within /BATCH mode. Defaults to `True`.\
    设置 MAPDL 在 /BATCH 模式下第一次出错时不终止。默认为 `True`。

    *force_intel* : *`bool`*
    : *(Development use only)* Forces the use of Intel message pass interface (MPI) in versions between Ansys 2021R0 and 2022R2, where because of VPNs issues this MPI is deactivated by default. See [Virtual private network (VPN) issues](https://mapdl.docs.pyansys.com/version/stable/user_guide/troubleshoot.html#vpn-issues-troubleshooting) for more information. Defaults to `False`.\
    在 Ansys 2021R0 和 2022R2 之间的版本中强制使用英特尔消息传递接口 (MPI)，由于 VPN 问题，默认情况下 MPI 已停用。更多信息请参阅 [虚拟专用网络 (VPN) 问题](https://mapdl.docs.pyansys.com/version/stable/user_guide/troubleshoot.html#vpn-issues-troubleshooting)。默认为 `False`。

    *log_broadcast* : *`bool`*
    : *(Only for CORBA mode)* Enables a logger to record broadcasted commands. Defaults to `False.`\
    启用记录仪记录广播命令。默认为 `False`。


Returns:
-------

  [`ansys.mapdl.core.mapdl._MapdlCore`](https://mapdl.docs.pyansys.com/version/stable/api/mapdl.html#ansys.mapdl.core.mapdl._MapdlCore)
  : An instance of Mapdl. Type depends on the selected `mode`.\
  Mapdl 的一个实例。类型取决于所选的 "模式"。

Return type:
-------------

  [`_MapdlCore`](https://mapdl.docs.pyansys.com/version/stable/api/mapdl.html#ansys.mapdl.core.mapdl._MapdlCore)
  :

Notes
--------

**Ansys Student Version**

If an Ansys Student version is detected, PyMAPDL will launch MAPDL in shared-memory parallelism (SMP) mode unless another option is specified.\
如果检测到 Ansys Student 版本，除非指定其他选项，否则 PyMAPDL 将以共享内存并行（SMP）模式启动 MAPDL。

**Additional switches**

These are the MAPDL switch options as of 2020R2 applicable for running MAPDL as a service via gRPC. Excluded switches such as `"-j"` either not applicable or are set via keyword arguments.\
这些是 2020R2 中适用于通过 gRPC 将 MAPDL 作为服务运行的 MAPDL 开关选项。排除在外的开关，如 `"-j"`，要么不适用，要么通过关键字参数设置。

- ***-acc<device>***

    Enables the use of GPU hardware. See GPU Accelerator Capability in the Parallel Processing Guide for more information.\
    启用 GPU 硬件。更多信息，请参阅《并行处理指南》中的 GPU 加速器功能。

- ***-amfg***

    Enables the additive manufacturing capability. Requires an additive manufacturing license. For general information about this feature, see AM Process Simulation in ANSYS Workbench.\
    启用快速成型制造功能。需要获得快速成型制造许可证。有关此功能的一般信息，请参阅 ANSYS Workbench 中的快速成型工艺仿真。

- ***-ansexe <executable>***

    Activates a custom mechanical APDL executable. In the ANSYS Workbench environment, activates a custom Mechanical APDL executable.\
    激活自定义 mechanical APDL 可执行文件。在 ANSYS 工作台环境中，激活自定义 mechanical APDL 可执行文件。

- ***-custom <executable>***

    Calls a custom Mechanical APDL executable See Running Your Custom Executable in the Programmer’s Reference for more information.\
    调用自定义 Mechanical APDL 可执行文件 更多信息，请参阅《程序员参考手册》中的 "运行自定义可执行文件"。

- ***-db value***

    Initial memory allocation Defines the portion of workspace (memory) to be used as the initial allocation for the database. The default is 1024 MB. Specify a negative number to force a fixed size throughout the run; useful on small memory systems.\
    初始内存分配 定义用作数据库初始分配的工作区（内存）部分。默认值为 1024 MB。指定一个负数可在整个运行过程中强制使用固定大小；在小内存系统中非常有用。

- ***-dis***

    Enables Distributed ANSYS See the Parallel Processing Guide for more information.\
    启用分布式 ANSYS 有关详细信息，请参阅并行处理指南。

- ***-dvt***

    Enables ANSYS DesignXplorer advanced task (add-on). Requires DesignXplorer.\
    启用 ANSYS DesignXplorer 高级任务（附加组件）。需要 DesignXplorer。

- ***-l <language>***

    Specifies a language file to use other than English This option is valid only if you have a translated message file in an appropriately named subdirectory in `/ansys_inc/v201/ansys/docu` or `Program Files\ANSYS\Inc\V201\ANSYS\docu`\
    指定要使用的非英语语言文件 该选项只有在"/ansys_inc/v201/ansys/docu`"或 "Program Files\ANSYS\Inc\V201\ANSYS\docu`"的适当命名子目录中有翻译的信息文件时才有效。

- ***-m <workspace>***

    Specifies the total size of the workspace Workspace (memory) in megabytes used for the initial allocation. If you omit the `-m` option, the default is 2 GB (2048 MB). Specify a negative number to force a fixed size throughout the run.\
    指定用于初始分配的工作区工作区（内存）的总大小（兆字节）。如果省略 `-m` 选项，默认值为 2 GB（2048 MB）。指定负数可强制在整个运行过程中使用固定大小。

- ***-machines <IP>***

    Specifies the distributed machines Machines on which to run a Distributed ANSYS analysis. See Starting Distributed ANSYS in the Parallel Processing Guide for more information.\
    指定运行分布式 ANSYS 分析的分布式机器。有关详细信息，请参阅并行处理指南中的启动分布式 ANSYS。

- ***-mpi <value>***

    Specifies the type of MPI to use. See the Parallel Processing Guide for more information.\
    指定要使用的 MPI 类型。更多信息，请参阅《并行处理指南》。

- ***-mpifile <appfile>***

    Specifies an existing MPI file Specifies an existing MPI file (appfile) to be used in a Distributed ANSYS run. See Using MPI Files in the Parallel Processing Guide for more information.\
    指定现有 MPI 文件 指定要在分布式 ANSYS 运行中使用的现有 MPI 文件（appfile）。有关详细信息，请参阅并行处理指南中的使用 MPI 文件。

- ***-na <value>***

    Specifies the number of GPU accelerator devices Number of GPU devices per machine or compute node when running with the GPU accelerator feature. See GPU Accelerator Capability in the Parallel Processing Guide for more information.\
    指定 GPU 加速器设备数量 使用 GPU 加速器功能运行时，每台机器或计算节点的 GPU 设备数量。更多信息，请参阅《并行处理指南》中的 GPU 加速器功能。

- ***-name <value>***

    Defines Mechanical APDL parameters Set mechanical APDL parameters at program start-up. The parameter name must be at least two characters long. For details about parameters, see the ANSYS Parametric Design Language Guide.\
    定义机械 APDL 参数 在程序启动时设置机械 APDL 参数。参数名称长度至少为两个字符。有关参数的详细信息，请参阅《ANSYS 参数化设计语言指南》。

- ***-p <productname>***

    ANSYS session product Defines the ANSYS session product that will run during the session. For more detailed information about the `-p` option, see Selecting an ANSYS Product via the Command Line.\
    ANSYS 会话产品 定义会话期间将运行的 ANSYS 会话产品。有关 `-p` 选项的详细信息，请参阅通过命令行选择 ANSYS 产品。

- ***-ppf <license feature name>***

    HPC license Specifies which HPC license to use during a parallel processing run. See HPC Licensing in the Parallel Processing Guide for more information.\
    HPC 许可证 指定并行处理运行期间要使用的 HPC 许可证。有关详细信息，请参阅《并行处理指南》中的 HPC 许可。

- ***-smp***

    Enables shared-memory parallelism. See the Parallel Processing Guide for more information.\
    启用共享内存并行。更多信息，请参阅《并行处理指南》。


If the environment is configured to use PyPIM and `start_instance` is `True`, then starting the instance will be delegated to PyPIM. In this event, most of the options will be ignored and the server side configuration will be used.\
如果环境配置为使用 PyPIM，且 `start_instance` 为 `True`，那么启动实例将委托给 PyPIM。在这种情况下，大部分选项将被忽略，并使用服务器端的配置。

Examples
----------

Launch MAPDL using the best protocol.\
使用最佳协议启动 MAPDL。

```python
>>> from ansys.mapdl.core import launch_mapdl
>>> mapdl = launch_mapdl()
```

Run MAPDL with shared memory parallel and specify the location of the Ansys binary.\
使用共享内存并行运行 MAPDL，并指定 Ansys 二进制文件的位置。

```python
>>> exec_file = 'C:/Program Files/ANSYS Inc/v231/ansys/bin/winx64/ANSYS231.exe'
>>> mapdl = launch_mapdl(exec_file, additional_switches='-smp')
```

Connect to an existing instance of MAPDL at IP 192.168.1.30 and port 50001. This is only available using the latest `'grpc'` mode.\
连接到 IP 地址为 192.168.1.30、端口为 50001 的现有 MAPDL 实例。这只能使用最新的 "grpc "模式。

```python
>>> mapdl = launch_mapdl(start_instance=False, ip='192.168.1.30',
                     port=50001)
```

Force the usage of the CORBA protocol.\
强制使用 CORBA 协议。

```python
>>> mapdl = launch_mapdl(mode='corba')
```

Run MAPDL using the console mode (available only on Linux).\
使用控制台模式运行 MAPDL（仅适用于 Linux）。

```python
mapdl = launch_mapdl('/ansys_inc/v194/ansys/bin/ansys194',
                      mode='console')
```



`````