# PyMAPDL 故障排除
为了帮助您解决在使用 PyMAPDL 时可能遇到的任何问题，这里发布了一些最常见的问题。

## Debug in PyMAPDL
如果在使用 PyMAPDL 时遇到麻烦，可以使用日志记录器将一些内部日志记录到文件中。可以检查此文件以帮助识别任何问题。

通过在 Python 终端或脚本开头运行以下命令，可以将 logger 输出文件设置为 `mylog.log`:

```python
from ansys.mapdl.core import LOG

LOG.setLevel("DEBUG")
LOG.log_to_file("mylog.log")

from ansys.mapdl.core import launch_mapdl

mapdl = launch_mapdl(loglevel="DEBUG")
```

你可以把这个文件附在 PyMAPDL GitHub 仓库的错误报告中，以便进一步调查。如果你不能确定问题，你可以在 (PyMAPDL Discussions page)(https://github.com/pyansys/PyMAPDL/discussions) 上新建一个讨论。如果你认为你已经发现了一个 bug，请在 (PyMAPDL Issues page)(https://github.com/pyansys/pymapdl/issues) 上打开一个 issue。

## 运行问题
有一些问题可能导致 MAPDL 无法启动，包括:


- [](Connection-timeout) (连接超时)
- [](Testing-MAPDL-launching) (测试MAPDL启动)
- [](Licensing-issues) (许可证问题)
- [](VPN-issues) (VPN问题)
- [](Missing-dependencies-on-Linux) (缺少对Linux的依赖)
- [](Conflicts-with-student-version) (与学生版本的冲突)
- [](Incorrect-environment-variables) (环境变量不正确)
- [](Using-a-proxy-server) (使用代理服务器)
- [](Firewall-settings) (防火墙设置)

(Connection-timeout)=
### Connection timeout
在某些网络中，MAPDL 连接到许可证服务器或远程实例的时间可能比预期的要长。在这些情况下，您可能会看到以下信息:

**PyMAPDL is taking longer than expected to connect to an MAPDL session. Checking if there are any available licenses…** (PyMAPDL 连接到一个 MAPDL 会话所花费的时间比预期的要长。)

在尝试其他选项之前，您可以考虑增加 `start timeout`(默认是 30s ):
```python
from ansys.mapdl.core import launch_mapdl

mapdl = launch_mapdl(start_timeout=60)
```

或者，如果连接到远程实例，则可以使用:

```python
from ansys.mapdl.core import Mapdl

mapdl = Mapdl(timeout=60)
```


(Testing-MAPDL-launching)=
### Testing MAPDL launching
在某些情况下，可能需要从命令行手动运行启动命令。

#### On Windows
打开命令提示符 (cmd) 并运行与版本相关的命令:

```
"C:\Program Files\ANSYS Inc\v211\ansys\bin\winx64\ANSYS211.exe"
```

```{note}
PowerShell 用户可以不使用引号运行前面的命令。
```
#### On Linux
运行版本相关的命令:

```
/usr/ansys_inc/v211/ansys/bin/ansys211
```

你应该在一个临时工作目录中启动 MAPDL，因为 MAPDL 会创建一些临时文件。

您可以通过从临时目录启动 MAPDL 来指定一个目录:

```
mkdir temporary_directory
cd temporary_directory
 & 'C:\Program Files\ANSYS Inc\v222\ansys\bin\winx64\ANSYS222.exe'
```

或者，您可以使用 `-dir` flag 标志指定目录:
```
mkdir temporary_directory
& 'C:\Program Files\ANSYS Inc\v222\ansys\bin\winx64\ANSYS222.exe' -dir "C:\ansys_job\mytest1"
```

如果这个命令没有启动 MAPDL，请查看命令输出:

```
(base) PS C:\Users\user\temp> & 'C:\Program Files\ANSYS Inc\v222\ansys\bin\winx64\ANSYS222.exe'
*** ERROR ***
Another Ansys job with the same job name (file) is already running in this
directory or the file.lock file has not been deleted from an abnormally
terminated Ansys run. To disable this check, set the ANSYS_LOCK environment
variable to OFF.
```


(Licensing-issues)=
### Licensing issues
不正确的许可证服务器配置会使 MAPDL 无法获得有效的许可证。在这种情况下，你可能会看到类似以下的输出：

```
(base) PS C:\Users\user\temp> & 'C:\Program Files\ANSYS Inc\v222\ansys\bin\winx64\ANSYS222.exe'

ANSYS LICENSE MANAGER ERROR:

Maximum licensed number of demo users already reached.


ANSYS LICENSE MANAGER ERROR:

Request name mech_2 does not exist in the licensing pool.
No such feature exists.
Feature:          mech_2
License path:  C:\Users\user\AppData\Local\Temp\\cb0400ba-6edb-4bb9-a333-41e7318c007d;
FlexNet Licensing error:-5,357
```

PADT 有一个关于 ANSYS 问题的很棒的博客，许可证一直是一个常见的问题。例如，请参阅 [ANSYS 2020R1上许可证的更改](https://www.padtinc.com/blog/15271-2/)。如果您负责维护 Ansys 许可证或者个人安装了 Ansys，请参阅 [Ansys 安装和许可文档](https://ansyshelp.ansys.com/account/secured?returnurl=/Views/Secured/prod_page.html?pn=Installation%20and%20Licensing&pid=InstallationAndLicensing&lang=en)。

要获得更全面的信息，请下载 *ANSYS Licensing Guide <licensing_guide_pdf_>*。

#### Incorrect licensing environment variables
不正确的许可环境变量

还可以使用环境变量 `ANSYSLMD_LICENSE_FILE` 指定许可证服务器。下面的代码示例展示了如何在 Windows 或 Linux 上查看这个环境变量的值。

**On Windows**

```
$env:ANSYSLMD_LICENSE_FILE
1055@1.1.1.1
```

**On Linux**

```
printenv | grep ANSYSLMD_LICENSE_FILE
```

(VPN-issues)=
### Virtual private network (VPN) issues
从 ANSYS 2022 R2 到 ANSYS 2021 R1，MAPDL 在运行 VPN 软件有启动问题。一个问题源于 MPI 通信，可以通过传递 `-smp` 选项将执行模式设置为 "共享内存并行"来解决，该选项**禁用了默认的"分布式内存并行"**。或者使用不同的 MPI 编译，例如，如果你使用的是 Windows，你可以通过`-mpi msmpi` 来使用微软的 MPI 库，而不是默认的 Intel MPI 库。这个问题不影响 Linux 版本的 MAPDL。

```{note}
如果你在 ANSYS 2022 R2 到 ANSYS 2021 R1 的任何一个版本中使用 Windows，当 MAPDL 实例由 PyMAPDL 启动时，默认的编译器是 Microsoft MPI。
```

```python
>>> from ansys.mapdl.core import launch_mapdl
>>> mapdl = launch_mapdl(additional_switches="-smp")
```

虽然这种方法的缺点是使用的较慢的共享内存并行模式，但你至少能够运行 MAPDL。关于共享内存与分布式内存的更多信息，请参见[High-Performance Computing for Mechanical Simulations using ANSYS](https://ansyshelp.ansys.com/account/secured?returnurl=/Views/Secured/corp/v222/en/ans_dan/dantoc.html) (使用 ANSYS 的高性能计算)。

此外，如果您的设备在 VPN 内，MAPDL 可能无法正确解决许可证服务器的 IP。验证许可证服务器的主机名或 IP 地址是否正确。

在 Windows 上，您可以在以下位置找到指向许可证服务器的许可证配置文件:

```
C:\Program Files\ANSYS Inc\Shared Files\Licensing\ansyslmd.ini
```


(Missing-dependencies-on-Linux)=
### Missing dependencies on Linux
一些 Linux 安装可能缺少必要的依赖项。如果你遇到 `libXp.so.6: cannot open shared object file: No such file or directory`这样的错误，你可能缺少一些必要的依赖项。

#### CentOS 7
在 CentOS 7上，你可以用以下方法安装缺失的依赖项：
```
yum install openssl openssh-clients mesa-libGL mesa-libGLU motif libgfortran
```

#### Ubuntu
在 Ubuntu 22.04 上，使用这段代码来安装所需的依赖项：
```
apt-get update

# Install dependencies
apt-get install -y \
openssh-client \
libgl1 \
libglu1 \
libxm4 \
libxi6
```

前面的代码处理了所有的事情，除了 `libxp6`，你必须用这段代码安装它：
```
# This is a workaround
# Source: https://bugs.launchpad.net/ubuntu/+source/libxp/+bug/1517884
apt install -y software-properties-common
add-apt-repository -y ppa:zeehio/libxp
apt-get update
apt-get install -y libxp6
```

#### Ubuntu 20.04 and older
如果你正在使用 Ubuntu 16.04，你可以用下面的代码安装 `libxp16`:
```
sudo apt install libxp6.
```

但是，如果您正在使用 Ubuntu 18.04 到 20.04，您必须手动下载并安装软件包。

因为 `libxpl6` 预先依赖于 `multiarch-support`，而后者也已经过时了，所以必须将其删除。否则,你的包配置就会出现故障。下面的代码下载并修改了 `libxp6` 包，删除了 `multiarch-support` 的依赖项，然后通过 `dpkg` 包进行安装。

```
cd /tmp
wget http://ftp.br.debian.org/debian/pool/main/libx/libxp/libxp6_1.0.2-2_amd64.deb
ar x libxp6_1.0.2-2_amd64.deb
sudo tar xzf control.tar.gz
sudo sed '/Pre-Depends/d' control -i
sudo bash -c "tar c postinst postrm md5sums control | gzip -c > control.tar.gz"
sudo ar rcs libxp6_1.0.2-2_amd64_mod.deb debian-binary control.tar.gz data.tar.xz
sudo dpkg -i ./libxp6_1.0.2-2_amd64_mod.deb
```

(Conflicts-with-student-version)=
### Conflicts with student version
尽管你可以将 Ansys 与其他 Ansys 产品或版本安装在一起，但在 Windows 上，你不应该将 Ansys 产品的学生版与非学生版安装在一起。例如，同时安装 Ansys MAPDL 2022 R2 学生版和 Ansys MAPDL 2022 R2 可能会因环境变量被覆盖而导致许可证冲突。拥有不同的版本，例如 Ansys MAPDL 2022 R2 学生版和Ansys MAPDL 2021 R1，是可以的。

如果遇到问题，你应该编辑这些环境变量，删除对学生版本的任何引用：`ANSYSXXX_DIR`，`AWP_ROOTXXX`，和 `CADOE_LIBDIRXXX`。请访问 [Incorrect environment variables](https://mapdl.docs.pyansys.com/version/stable/user_guide/troubleshoot.html#incorrect-environment-variables)(不正确的环境变量)，了解如何将这些环境变量设置到正确的位置。

```{note}
启动 MAPDL 学生版本默认情况下，如果检测到学生版本， PyMAPDL 将以 `SMP` 模式启动 MAPDL 实例，除非指定了另一个 MPI 选项。
```

(Incorrect-environment-variables)=
### Incorrect environment variables
如果你使用非标准的安装方式，你可能需要手动设置环境变量 `ANSYSXXX_DIR`、`AWP_ROOTXXX` 和 `CADOE_LIBDIRXXX` 到正确位置。三位数的 MAPDL 版本号出现在显示 `XXX` 的地方。例如对于 Ansys MAPDL 2022 R2，`222` 出现在显示 `XXX` 的地方。

```
PS echo $env:AWP_ROOT222
C:\Program Files\ANSYS Inc\ANSYS Student\v222
PS $env:AWP_ROOT222 = "C:\Program Files\ANSYS Inc\v222"  # This overwrites the env var for the terminal session only.
PS [System.Environment]::SetEnvironmentVariable('AWP_ROOT222','C:\Program Files\ANSYS Inc\v222',[System.EnvironmentVariableTarget]::User)  # This changes the env var permanently.
PS echo $env:AWP_ROOT222
C:\Program Files\ANSYS Inc\v222

PS echo $env:ANSYS222_DIR
C:\Program Files\ANSYS Inc\ANSYS Student\v222\ANSYS
PS [System.Environment]::SetEnvironmentVariable('ANSYS222_DIR','C:\Program Files\ANSYS Inc\v222\ANSYS',[System.EnvironmentVariableTarget]::User)
PS echo $env:ANSYS222_DIR
C:\Program Files\ANSYS Inc\v222\ANSYS

PS echo $env:CADOE_LIBDIR222
C:\Program Files\ANSYS Inc\ANSYS Student\v222\CommonFiles\Language\en-us
PS [System.Environment]::SetEnvironmentVariable('CADOE_LIBDIR222','C:\Program Files\ANSYS Inc\v222\CommonFiles\Language\en-us',[System.EnvironmentVariableTarget]::User)
PS echo $env:CADOE_LIBDIR222
C:\Program Files\ANSYS Inc\v222\CommonFiles\Language\en-us
```

(Using-a-proxy-server)=
### Using a proxy server
在某些罕见的情况下，如果你使用代理，你可能会遇到一些连接到 MAPDL 实例的问题。当 gRPC 在代理环境中使用时，如果指定一个本地地址（即 `127.0.0.1` ）作为连接目的地，gRPC 的实现会自动引用代理地址。在这种情况下，无法引用本地地址，从而导致连接错误。作为一种解决方法，你可以将环境变量 `NO_PROXY` 设置为你的本地地址 `127.0.0.1`，然后运行 **`launch_mapdl()`** 来连接到 MAPDL 实例。


(Firewall-settings)=
### Firewall settings
MAPDL 和 Python 应该有正确的防火墙设置，以允许两者之间的通信。如果您使用的是防火墙，您应该允许 MAPDL 接收以下端口的入站连接：

- 5005X (TCP) for gRPC connections.
- 50055 (TCP) for gRPC connection to the MAPDL database.
- 1055 (TCP) for licensing connections.
- 2325 (TCP) for licensing connections.

必须允许 Python 进程连接到所提到的端口（外向连接）。

通常情况下，大多数防火墙规则都集中在入站连接上，所以你应该不需要配置出站连接。然而，如果你遇到了问题，你应该确保防火墙没有阻止以下端口的出站连接：

- 5005X (TCP) for gRPC connections.
- 50055 (TCP) for gRPC connection to the MAPDL database.
- 1055 (TCP) for licensing connections.
- 2325 (TCP) for licensing connections.

有关**如何在 Windows 上配置防火墙**的详细信息，请参阅 Ansys 论坛中的以下链接:[许可证2022 R2 Linux Ubuntu (以及 Windows)](https://forum.ansys.com/forums/topic/licensing-2022-r2-linux-ubuntu-and-also-windows/)。

关于**如何在 Ubuntu Linux 上配置防火墙**的更多信息，请参考以下链接 [Security-Firewall | Ubuntu](https://ubuntu.com/server/docs/security-firewall)。

## 手动设置可执行文件的位置
如果你有一个非标准的安装，PyMAPDL 可能无法找到你的 MAPDL 安装位置。如果是这种情况，请提供 MAPDL 的位置作为 **`launch_mapdl()`** 的第一个参数。

**On Windows**
```
>>> from ansys.mapdl.core import launch_mapdl
>>> exec_loc = "C:/Program Files/ANSYS Inc/v211/ansys/bin/winx64/ANSYS211.exe"
>>> mapdl = launch_mapdl(exec_loc)
```

**On Linux**
```
>>> from ansys.mapdl.core import launch_mapdl
>>> exec_loc = "/usr/ansys_inc/v211/ansys/bin/ansys211"
>>> mapdl = launch_mapdl(exec_loc)
```

### 可执行文件的默认位置
当你第一次运行 PyMAPDL 时，它会检测可用的 Ansys 安装程序。

**On Windows**

Ansys的安装程序通常是在：

```
C:/Program Files/ANSYS Inc/vXXX
```

**On Linux**

Ansys的安装程序通常是在：

```
/usr/ansys_inc/vXXX
```
Or 是在:
```
/ansys_inc/vXXX
```

默认情况下，Ansys 安装程序使用前一个(`/usr/ansys_inc`)，但也创建一个符号到后一个(`/ansys_inc`)。

如果 PyMAPDL 找到一个有效的 Ansys 安装程序，它会将其路径缓存在配置文件 `config.txt` 中。该文件的路径显示在下面的代码中:

```python
>>> from ansys.mapdl.core.launcher import CONFIG_FILE
>>> print(CONFIG_FILE)
'C:\\Users\\user\\AppData\\Local\\ansys_mapdl_core\\ansys_mapdl_core\\config.txt'
```

在某些情况下，这个配置文件可能会变得过时。例如，当一个新的 Ansys 版本被安装，而早期的安装就会被删除。

要用最新的路径更新这个配置文件，请使用：

```python
>>> from ansys.mapdl.core import save_ansys_path
>>> save_ansys_path(r"C:\Program Files\ANSYS Inc\v222\ansys\bin\winx64\ansys222.exe")
'C:\\Program Files\\ANSYS Inc\\v222\\ansys\\bin\\winx64\\ansys222.exe'
```

如果你想看看 PyMAPDL 检测到了哪些 Ansys 安装，请使用：

```python
>>> from ansys.mapdl.core.launcher import get_available_ansys_installations
>>> get_available_ansys_installations()
{222: 'C:\\Program Files\\ANSYS Inc\\v222',
212: 'C:\\Program Files\\ANSYS Inc\\v212',
-222: 'C:\\Program Files\\ANSYS Inc\\ANSYS Student\\v222'}
```

因为 Python 字典不接受两个相等的 key，所以学生版本是 **negative** version。**`get_ability_ansys_install()`** 方法的结果首先列出较高版本，最后列出学生版本。

```{warning}
您不应该安装相同的 Ansys 产品版本和学生版本。有关更多信息，请参见与 [学生版本的冲突](Conflicts-with-student-version)。
```

## PyMAPDL 使用问题

### 在 MAPDL 中导入和导出 numpy 数组时出现的问题
由于 MAPDL 的设计方式，没有办法存储一个或多个维度为零的数组。这可能发生在 numpy 数组中，它的第一维可以被设置为零。比如说：

```python
>>> import numpy
>>> from ansys.mapdl.core import launch_mapdl
>>> mapdl = launch_mapdl()
>>> my_array = np.reshape([1, 2, 3, 4], (4,))
>>> my_array
array([1, 2, 3, 4])
```

这些类型的数组维度总是转换为 `1`。

例如:

```python
>>> mapdl.parameters["mapdlarray"] = my_array
>>> mapdl.parameters["mapdlarray"]
array([[1.],
   [2.],
   [3.],
   [4.]])
>>> mapdl.parameters["mapdlarray"].shape
(4, 1)
```

这意味着当你传递两个数组时，一个数组的第二轴等于0（例如 `my_array`），另一个数组的第二轴等于 1 ，如果稍后检索的话，则具有相同的形状。

```python
>>> my_other_array = np.reshape([1, 2, 3, 4], (4, 1))
>>> my_other_array
array([[1],
   [2],
   [3],
   [4]])
>>> mapdl.parameters["mapdlarray_b"] = my_other_array
>>> mapdl.parameters["mapdlarray_b"]
array([[1.],
   [2.],
   [3.],
   [4.]])
>>> np.allclose(mapdl.parameters["mapdlarray"], mapdl.parameters["mapdlarray_b"])
True
```

## PyMAPDL 稳定性

### 建议
当使用 gRPC (默认)连接到 MAPDL 实例时，有些情况下 MAPDL 服务器可能意外退出。有几种方法可以提高 MADPL 的性能和稳定性:

使用 `mute` 来提高稳定性

如果可能，将 `mute=True` 传递给各个 MAPDL 命令，或者用 **`Mapdl.mute`** 方法全局地设置它。这将禁止从 MAPDL 流回每个命令的响应，并略微提高性能和稳定性。考虑在你的程序或脚本中设置一个调试标志，以便根据需要打开和关闭日志记录和详细信息。

### Issues
```{note}
MAPDL 2021 R1 的 **`Mapdl.input()`** 方法有一个稳定性问题。如果可能的话，避免使用输入文件。尝试使用 **`Mapdl.upload()`** 方法来上传节点和元素，并通过 **`Mapdl.nread()`** 和 **`Mapdl.eread()`** 方法将其读入。
```

**More help needed?**

> “What do you do if a problem is not listed here?”

进入 [PyMAPDL Issues](https://github.com/pyansys/pymapdl/issues) 页面并搜索，看看你的问题是否已经被列出。如果没有，你可以采取以下措施之一：

- 转到 [PyMAPDL Discussions](https://github.com/pyansys/PyMAPDL/discussions)页面，创建一个关于您的问题的讨论。
- 如果您发现了一个 bug 或者想要创建一个特性请求，请转到 [PyMAPDL Issues](https://github.com/pyansys/pymapdl/issues)。

对于更复杂的问题或查询，请联系 pyansys.support@ansys.com。