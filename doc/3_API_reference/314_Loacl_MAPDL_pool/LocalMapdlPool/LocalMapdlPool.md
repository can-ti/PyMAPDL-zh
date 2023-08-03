# LocalMapdlPool

````{class} ansys.mapdl.core.pool.LocalMapdlPool(n_instances, wait=True, run_location=None, port=50052, progress_bar=True, restart_failed=True, remove_temp_files=True, **kwargs)

Create a pool of MAPDL instances.

```{note}
Requires MAPDL 2020 R2 or later.
```

Parameters:
-----------

  n_instance : *`int`*
  : Number of instances to create.\
  要创建的实例数量。

  wait : *`bool`* , *`optional`*
  : Wait for pool to be initialized. Otherwise, pool will start in the background and all resources may not be available instantly.\
  等待池初始化。否则，池会在后台启动，所有资源可能无法立即可用。

  run_location : *`str`* , *`optional`*
  : Base directory to create additional directories for each MAPDL instance. Defaults to a temporary working directory.\
  为每个 MAPDL 实例创建附加目录的基本目录。默认为临时工作目录。

  starting_port : *`int`* , *`optional`*
  : Starting port for the MAPDL instances. Defaults to 50052.\
  MAPDL 实例的起始端口。默认为 50052。

  progress_bar : *`bool`* , *`optional`*
  : Show a progress bar when starting the pool. Defaults to `True`. Will not be shown when `wait=False`.\
  启动池时显示进度条。默认为 `True`。当 `wait=False` 时不会显示。

  restart_failed : *`bool`* , *`optional`*
  : Restarts failed instances. Defaults to `True`.\
  重启动失败的实例。默认为 `True`。

  remove_temp_files : *`bool`* , *`optional`*
  : This launcher creates a new MAPDL working directory for each instance of MAPDL within the temporary user directory, obtainable with `tempfile.gettempdir()`, for MAPDL files. When this parameter is `True`, this directory will be deleted when MAPDL is exited. Default `False`.\
  该启动器会为每个 MAPDL 实例在临时用户目录内创建一个新的 MAPDL 工作目录，该目录可通过 `tempfile.gettempdir()` 获得，用于存放 MAPDL 文件。如果此参数为 `True`，则在退出 MAPDL 时删除此目录。默认为 `False`。

  **kwargs : *`dict`* , *`optional`*
  : See `ansys.mapdl.core.launch_mapdl()` for a complete listing of all additional keyword arguments.\
  有关所有附加关键字参数的完整列表，请参阅 `ansys.mapdl.core.launch_mapdl()` 。

Examples
----------

Simply create a pool of 10 instances to run in the temporary directory.\
只需在临时目录中创建一个由 10 个实例组成的运行池。

```python
>>> from ansys.mapdl.core import LocalMapdlPool
>>> pool = LocalMapdlPool(10)
Creating Pool: 100%|########| 10/10 [00:01<00:00,  1.43it/s]
```

Create several instances with 1 CPU each running at the current directory within their own isolated directories.\
在当前目录下创建多个实例，每个实例有 1 个 CPU，运行在各自独立的目录中。

```python
>>> import os
>>> my_path = os.getcmd()
>>> pool = LocalMapdlPool(10, nproc=1, run_location=my_path)
Creating Pool: 100%|########| 10/10 [00:01<00:00,  1.43it/s]
```

Create a pool while specifying the MAPDL executable in Windows.\
在 Windows 中指定 MAPDL 可执行文件时创建池。

```python
>>> exec_file = 'C:/Program Files/ANSYS Inc/v212/ansys/bin/winx64/ANSYS212.exe'
>>> pool = LocalMapdlPool(10, exec_file=exec_file)
Creating Pool: 100%|########| 10/10 [00:01<00:00,  1.43it/s]
```

Create a pool while specifying the MAPDL executable in Linux.\
在 Linux 中指定 MAPDL 可执行文件时创建池。

```python
>>> exec_file = '/ansys_inc/v211/ansys/bin/ansys211'
>>> pool = LocalMapdlPool(10, exec_file=exec_file)
Creating Pool: 100%|########| 10/10 [00:01<00:00,  1.43it/s]
```

Methods
-------

```{table}
| | | |
|---|---|---|
| {doc}`LocalMapdlPool.exit([block]) <../LocalMapdlPool/exit>` | Close out all instances in the pool. | 关闭池中的所有实例。 |
| {doc}`LocalMapdlPool.map(func[, iterable, ...]) <../LocalMapdlPool/map>` | Run a function for each instance of mapdl within the pool. | 为池中的每个 mapdl 实例运行一个函数。 |
| {doc}`LocalMapdlPool.next_available([return_index]) <../LocalMapdlPool/next_available>` | Wait until an instance of mapdl is available and return that instance. | 等待 mapdl 实例可用，并返回该实例。 |
| {doc}`LocalMapdlPool.run_batch(files[, ...]) <../LocalMapdlPool/run_batch>` | Run a batch of input files on the pool. | 在池上运行一批输入文件。 |
```


````