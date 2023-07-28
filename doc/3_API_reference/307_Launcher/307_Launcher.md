# Launcher

Various PyMAPDL specific launcher commands. Most of these commands are called from the library [ansys-tools-path](http://path.tools.docs.pyansys.com/).\
各种 PyMAPDL 特定的启动器命令。这些命令大多从 ansys-tools-path 库中调用。

```{table}

| | | |
|---|---|---|
| {doc}`get_default_ansys() <../307_Launcher/get_default_ansys>`  | Searches for ansys path within the standard install location and returns the path and version of the latest MAPDL version installed. | 在标准安装位置内搜索 ansys 路径，并返回已安装的最新 MAPDL 版本的路径和版本号。 |
| {doc}`get_default_ansys_path() <../307_Launcher/get_default_ansys_path>` | Searches for ansys path within the standard install location and returns the path of the latest MAPDL version installed. | 在标准安装位置内搜索 ansys 路径，并返回已安装的最新 MAPDL 版本的路径。 |
| {doc}`get_default_ansys_version() <../307_Launcher/get_default_ansys_version>` | Searches for ansys path within the standard install location and returns the version of the latest MAPDL version installed. | 在标准安装位置内搜索 ansys 路径，并返回已安装的最新 MAPDL 版本的版本号。 |
| {doc}`launch_mapdl([exec_file, run_location, ...]) <../307_Launcher/launch_mapdl>` | Start MAPDL locally. | 在本地启动 MAPDL。 |
| {doc}`close_all_local_instances([port_range]) <../307_Launcher/close_all_local_instances>` | Close all MAPDL instances within a port_range. | 关闭端口范围内的所有 MAPDL 实例。 |


```

## `ansys-tools-path` functions

```{table}

| | | |
|---|---|---|
| {doc}`change_default_ansys_path(exe_loc) <../307_Launcher/change_default_ansys_path>`  | Deprecated, use `change_default_mapdl_path` instead | 已弃用，请使用 `change_default_mapdl_path` 代替 |
| {doc}`find_ansys([version, supported_versions]) <../307_Launcher/find_ansys>` | Obsolete method, use `find_mapdl`. | 方法已过时，请使用 `find_mapdl`。 |
| {doc}`save_ansys_path([exe_loc, allow_prompt]) <../307_Launcher/save_ansys_path>` | Deprecated, use `save_mapdl_path` instead | 已弃用，请使用 `save_mapdl_path` 代替。 |
| {doc}`get_available_ansys_installations([...]) <../307_Launcher/get_available_ansys_installations>` | Return a dictionary of available Ansys unified installation versions with their base paths. | 返回可用的 Ansys 统一安装版本及其基本路径的字典。 |


```