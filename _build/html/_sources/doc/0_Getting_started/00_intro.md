# 开始

要使用 PyMAPDL，您必须在本地安装 Ansys。安装的 Ansys 版本决定了可用的接口和特性。

有关获得 Ansys 授权副本的更多信息，请访问 [Ansys](https://www.ansys.com/)。

## 安装

### Python 模块

`ansys.mapdl.core` 包目前在 Windows、 Mac OS 和 Linux 上支持 Python 3.7 到 Python 3.10。

使用以下命令安装 [PyPi](https://pypi.org/project/ansys-mapdl-core/) 的最新版本:

```python
pip install ansys-mapdl-core
```

或者，通过以下方式从 [PyMAPDL GitHub](https://github.com/pyansys/pymapdl/issues) 安装最新版本:

```
pip install git+https://github.com/pyansys/pymapdl.git
```

对于本地开发版本，安装时使用:

```python
git clone https://github.com/pyansys/pymapdl.git
cd pymapdl
pip install -e .
```

这允许您安装 `ansys-mapdl-core` 模块并可以在本地修改它，重新启动 Python 内核后将更改反映在您的设置中。

### 离线安装
如果您的电脑上没有互联网连接，安装 PyMAPDL 的推荐方法是从[版本页面](https://github.com/pyansys/pymapdl/releases)下载相应系统版本的 wheelhouse archive。

每个 wheelhouse 库都包含了在 Windows 和 Linux 上为 Python 3.7 和 3.9 安装 PyMAPDL 所需的所有 Python wheelhouse。你可以在一个有 Python 的独立系统上或在一个虚拟环境中安装。

例如，在使用 Python 3.7 的 Linux 上，解压缩并使用以下代码进行安装:

```
unzip PyMAPDL-v0.62.dev1-wheelhouse-Linux-3.7.zip wheelhouse
pip install ansys-mapdl-core -f wheelhouse --no-index --upgrade --ignore-installed
```

如果你在 Windows 上使用 Python 3.9，解压`wheelhouse` 到一个控制目录并使用前面的命令进行安装。

考虑使用虚拟环境进行安装。

### Ansys软件需求
对于最新的特性，您必须在本地安装 Ansys2021R1的副本。但是，PyMAPDL 与 Ansys 17.0和 Windows 上的更高版本以及 Linux 上的 Ansys 13.0兼容。

```{note}
Ansys 的最新版本提供了更好的支持和特性。早期的 Ansys 版本不支持某些特性，比如 APDLMath。
```

有关更多信息，请参见[安装 MAPDL](https://mapdl.docs.pyansys.com/version/stable/getting_started/running_mapdl.html#install-mapdl)。

### 验证你的安装
检查是否可以通过运行以下命令从 Python 启动 MAPDL:

```{code-cell} python
from ansys.mapdl.core import launch_mapdl
mapdl = launch_mapdl()
print(mapdl)

Product:             ANSYS Mechanical Enterprise
MAPDL Version:       RELEASE  2021 R1           BUILD 21.0
PyMAPDL Version:     Version: 0.58.0
```

如果您看到来自服务器的响应，那么祝贺您。您已经准备好开始使用 MAPDL 作为服务。有关 PyMAPDL 接口的信息，请参见 [PyMAPDL 语言和使用](https://mapdl.docs.pyansys.com/version/stable/user_guide/mapdl.html#ref-mapdl-user-guide)。


