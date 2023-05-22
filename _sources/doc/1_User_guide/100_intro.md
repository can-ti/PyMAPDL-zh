# 用户指南
本节提供了 PyMAPDL 的总体概述以及如何使用它。

## PyMAPDL 概述
`ansys-mapdl-core` 库中的 **`launch_mapdl()`** 函数在后台创建一个 **`Mapdl`** 类的实例，并向该服务发送命令。错误和警告会以 Python 的方式处理，让您可以实时开发一个脚本，而不必担心它在批处理模式下部署时是否正常。

可以使用 **`launch_mapdl()`** 方法从 Python 中以 gRPC 模式启动 MAPDL。默认情况下，这将在一个临时目录下启动 MAPDL。您可以用以下方法将其改为您的当前目录：
``` python
import os
from ansys.mapdl.core import launch_mapdl

path = os.getcwd()
mapdl = launch_mapdl(run_location=path)
```

MAPDL 现在是活动的，你可以像一个真正的 Python class 一样向它发送命令。例如，如果你想用关键点来创建一个曲面，你可以运行：

``` python
mapdl.run("/PREP7")
mapdl.run("K, 1, 0, 0, 0")
mapdl.run("K, 2, 1, 0, 0")
mapdl.run("K, 3, 1, 1, 0")
mapdl.run("K, 4, 0, 1, 0")
mapdl.run("L, 1, 2")
mapdl.run("L, 2, 3")
mapdl.run("L, 3, 4")
mapdl.run("L, 4, 1")
mapdl.run("AL, 1, 2, 3, 4")
```

MAPDL 会交互式地返回每条命令的结果，这些结果被存储到日志模块中。错误会被立即捕获。例如，如果你输入一个无效的命令：

``` python
>>> mapdl.run("AL, 1, 2, 3")

apdlRuntimeError:
L, 1, 2, 3

EFINE AREA BY LIST OF LINES
INE LIST =     1    2    3
TRAVERSED IN SAME DIRECTION AS LINE     1)

** ERROR ***                           CP =       0.338   TIME= 09:45:36
eypoint 1 is referenced by only one line.  Improperly connected line
et for AL command.
```

这个 `MapdlRuntimeError` 将被立即捕获。这意味着你可以用 Python 编写 MAPDL 脚本，以交互方式运行，然后以批处理方式运行，而不必担心如果你把脚本输出到一个脚本文件中，该脚本是否会正确运行。

Mapdl 类支持的不仅仅是向 MAPDL 发送文本。它包括更高层次的包装，允许更好地编写脚本和与 MAPDL 互动。关于可视化、编写脚本以及与 MAPDL 交互的各种高级方法的概述，请参见[示例](https://mapdl.docs.pyansys.com/version/stable/examples/index.html#ref-examples)。

## 用 Python 调用 MAPDL
MAPDL 函数可以直接从 `Mapdl` 的实例中以 Pythonic 方式调用。这是为了简化调用 Ansys，特别是当输入的是 Python 中的变量时。例如，以下两个命令是等价的：

``` python
mapdl.k(1, 0, 0, 0)
mapdl.run("K, 1, 0, 0, 0")
```

这种方法有一些明显的优势。首先，它更容易编写脚本，因为 `Ansys-mapdl-core` 为你处理了字符串格式化的问题。例如，你可以用以下方法从一个 numpy 数组中输入点：
``` python
# make 10 random keypoints in Ansys
points = np.random.random((10, 3))
for i, (x, y, z) in enumerate(points):
    mapdl.k(i + 1, x, y, z)
```

此外，错误会在 Python 中捕获和处理。

``` 
>>> mapdl.run("AL, 1, 2, 3")

xception:
L, 1, 2, 3

EFINE AREA BY LIST OF LINES
INE LIST =     1    2    3
TRAVERSED IN SAME DIRECTION AS LINE     1)

** ERROR ***                           CP =       0.338   TIME= 09:45:36
eypoint 1 is referenced by only one line.  Improperly connected line
et for AL command.
```

对于较长的脚本，不要像在创建 area 的例子中那样向 MAPDL 发送命令，而是可以这样运行：

``` py
# clear existing geometry
mapdl.finish()
mapdl.clear()

# create a square area using keypoints
mapdl.prep7()
mapdl.k(1, 0, 0, 0)
mapdl.k(2, 1, 0, 0)
mapdl.k(3, 1, 1, 0)
mapdl.k(4, 0, 1, 0)
mapdl.l(1, 2)
mapdl.l(2, 3)
mapdl.l(3, 4)
mapdl.l(4, 1)
mapdl.al(1, 2, 3, 4)
```

这种方法有一些明显的优势，主要是它的脚本比较容易，因为 Mapdl 为你处理了字符串的格式化。例如，从一个 numpy 数组中输入点：

``` py
import numpy as np

# make 10 random keypoints in MAPDL
points = np.random.random((10, 3))
for i, (x, y, z) in enumerate(points):
    mapdl.k(i + 1, x, y, z)
```

此外，MAPDL 类中的每个函数都有相关的帮助。例如:

```py
>>> help(mapdl.k)

Help on method K in module ansys.mapdl.core.mapdl_grpc.MapdlGrpc:

k(npt='', x='', y='', z='') method of ansys.mapdl.core.mapdl_grpc.MapdlGrpc
instance

    Defines a keypoint.

    APDL Command: K

    Parameters
    ----------
    npt
        Reference number for keypoint. If zero, the lowest
        available number is assigned [NUMSTR].

    x, y, z
        Keypoint location in the active coordinate system (may be
        R, θ, Z or R, θ, Φ). If X = P, graphical picking is
        enabled and all other fields (including NPT) are ignored
        (valid only in the GUI).

    Examples
    --------
    Create a keypoint at (1, 1, 2)

>>> mapdl.k(1, 1, 1, 2)

    Notes
    -----
    Defines a keypoint in the active coordinate system [CSYS] for
    line, area, and volume descriptions. A previously defined
    keypoint of the same number is then redefined. A keypoint may
    be redefined only if it is not yet attached to a line or is
    not yet meshed. Solid modeling in a toroidal system is not
    recommended.
```

有关稳定性的考虑，请参见 [PyMAPDL 稳定性](https://mapdl.docs.pyansys.com/version/stable/user_guide/troubleshoot.html#ref-pymapdl-stability)。

