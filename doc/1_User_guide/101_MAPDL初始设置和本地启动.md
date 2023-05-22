# MAPDL 初始设置和本地启动
要运行，`ansys.mapdl.core` 必须知道 **MAPDL** 二进制文件的位置。大多数情况下，这可以自动确定，但对于非标准的安装，必须提供 **MAPDL** 的本地位置。当第一次运行时，如果不能自动找到 **MAPDL**，`ansys-mapdl-core` 会请求提供 **`MAPDL`** 的可执行文件的位置。你可以通过运行 **`launch_mapdl()`** 函数来测试你的PyMAPDL的安装和设置：

``` py
from ansys.mapdl.core import launch_mapdl

mapdl = launch_mapdl()
```

Python 会自动尝试基于环境变量检测 MAPDL 二进制文件。如果无法找到 MAPDL 的副本，系统将提示您输入 MAPDL 可执行文件的位置。

下面是 Linux 的一个输入示例:

```{code-block} 
Enter location of MAPDL executable: /usr/ansys_inc/v222/ansys/bin/ansys222
```

下面是 Windows 的一个输入示例:

```
Enter location of MAPDL executable: C:\Program Files\ANSYS Inc\v222\ANSYS\bin\winx64\ansys222.exe
```

设置文件存储在本地，这意味着不会提示您再次输入路径。如果必须更改默认的 Ansys 路径(即想要更改 MAPDL 的默认版本) ，请运行以下命令:

```python
from ansys.mapdl import core as pymapdl

new_path = "C:\\Program Files\\ANSYS Inc\\v212\\ANSYS\\bin\\winx64\\ansys222.exe"
pymapdl.change_default_ansys_path(new_path)
```

另请参见 **`change_default_ansys_path()`** 方法和 **`find_ansys()`** 方法。

此外，还可以使用关键字参数 `exec_file` 指定可执行文件。

In Linux:
```py
from ansys.mapdl.core import launch_mapdl

mapdl = launch_mapdl(exec_file="/usr/ansys_inc/v212/ansys/bin/ansys212")
```

In Windows:
```py
from ansys.mapdl.core import launch_mapdl

mapdl = launch_mapdl(
    exec_file="C://Program Files//ANSYS Inc//v212//ANSYS//bin//winx64//ansys212.exe"
)
```

您还可以通过将对应的标志(`-custom`)添加到 `additional_switch` 关键字参数中来指定自定义可执行文件:

```py
from ansys.mapdl.core import launch_mapdl

custom_exec = "/usr/ansys_inc/v212/ansys/bin/ansys212t"
add_switch = f" -custom {custom_exec}"
mapdl = launch_mapdl(additional_switches=add_switch)
```

## API 接口
有关控制 MAPDL 如何在本地启动的更多信息，请参见 **`launch_MAPDL()`** 函数的说明。


