# 使用 Python 编写 UPF 子程序

作为 C 和 Fortran 这样的编译语言的替代品，你现在可以使用 Python 语言来编码用户可编程子程序(UPF)。已文档化的 UPF 子程序的一个子集支持 Python UPF 功能。更多信息，请参见 [Supported UPF subroutinues](https://mapdl.docs.pyansys.com/version/stable/user_guide/upf.html#supported-upf-subroutines) (支持的UPF子程序)。

在使用这个功能之前，你必须安装一个 Python 发行版。支持 Python 3.6 到 Python 3.7。

**Python UPF 只支持 Linux 系统。**

我们强烈建议你基于 [Python UPF examples](https://mapdl.docs.pyansys.com/version/stable/user_guide/upf.html#python-upf-examples) 中的一个例子开始你的代码。在你的 Python 代码中，可以使用如 NumPy 之类的标准 Python 库。

以下这些主题可供参考:

- [](heading113_1)
- [](heading113_2)
- [](heading113_3)
- [](heading113_4)
- [](heading113_5)


(heading113_1)=
## Supported UPF subroutines
整个可用的 UPF 子程序集的一个子集支持 Python 编码。下表列出了那些被支持的程序。

```{table} Python support for subroutines

| Subroutine(子程序) |Fortran description|
| --- | --- |
|**Material behavior**| |
| `UserMat` | Subroutine `UserMat` (Creating Your Own Material Model) |
| `UserMatTh` | Subroutine `UserMatTh` (Creating Your Own Thermal Material Model) |
| `UserHyper` | Subroutine `UserHyper` (Writing Your Own Isotropic Hyperelasticity Laws(各向同性超弹性定律)) |
| `UserCreep` | Subroutine `UserCreep` (Defining Creep Material Behavior) |
|**Modifying and Monitoring Elements**| |
| `UsrShift` | Subroutine `UsrShift` (Calculating Pseudotime Time Increment) |
| `UTimeInc` | Subroutine `UTimeInc` (Overriding the Program-Determined Time Step) |
| `Ucnvrg` | Subroutine `UCnvrg` (Overriding the Program-Determined Convergence) |
|**Customizing loads**| |
| `usrefl` | Subroutine `usrefl` (Changing Scalar Fields to User-Defined Values) |
| `userpr` | Subroutine `userpr` (Changing Element Pressure Information) |
| `usercv` | Subroutine `usercv` (Changing Element Face Convection Surface Information) |
| `userfx` | Subroutine `userfx` (Changing Element Face Heat Flux Surface Information) |
|**Accessing subroutines** |Access at the beginning and end of various operations|
| `UanBeg` / `UanFin` | |
| `USolBeg` / `USolFin` | |
| `ULdBeg` / `ULdFin` | |
| `UItBeg` / `UItFin` | |
| `USsBeg` / `USsFin` | |

```

(heading113_2)=
## Python UPF methodology
编码 Python UPF 与使用 C/C++ 或 Fortran 等编译语言不同，主要体现在 API 方面。因为 [gRPC 技术](https://grpc.io/)是用来处理 Python 进程和 Mechanical APDL 进程之间的通信和数据交换的，你需要了解这个功能处理数据的序列化和反序列化的方式。

主要的区别在于子程序的参数。每个子程序都有一个完整的参数列表，而不是像描述的那样，只有两个参数：请求对象（用于输入）和响应对象（用于输出）。如果一个参数既是子程序的输入又是输出，它就都是这两个对象的一部分。

有关"请求对象"和"响应对象"的描述可以在这个安装目录下存储的 `MapdlUser.proto` 文件中找到：

```
Ansys Inc\vXXX\ansys\syslib\ansGRPC\User
```

其中 XXX 是您正在使用的 Mechanical APDL 的版本。例如 `222` 代表 Mechanical APDL 2022R2。

首先，从这个模板开始创建一个 Python 文件:

```{code-block} python
:caption:  my_upf.py

import grpc
import sys
from mapdl import *


class MapdlUserService(MapdlUser_pb2_grpc.MapdlUserServiceServicer):
    #   #################################################################
    def UAnBeg(self, request, context):
        print(" ======================================= ")
        print(" >> Inside the PYTHON UAnBeg routine  << ")
        print(" ======================================= \n")

        response = google_dot_protobuf_dot_empty__pb2._EMPTY()
        return response


if __name__ == "__main__":
    upf.launch(sys.argv[0])
```

请注意，Mechanical APDL 会自动安装 Mechanical APDL Python package（一组Python函数），以处理 Mechanical APDL 和 Python 环境之间的连接。每个 Python UPF 都必须被导入：

```python
from mapdl import *
```

要使用这个 Python UPF，你必须将 Mechanical APDL `/UPF` 命令添加到你的输入文件（`my/_inp.dat`）。

```
/UPF,'my_upf.py'

! The UAnBeg UPF must be activated by using the USRCAL APDL command

USRCAL,UANBEG
```

该命令被 Mechanical APDL Launcher 捕获，因这样当 Mechanical APDL 进程启动时，Python gRPC 服务器就可以启动并运行了。

当使用这个输入文件启动 Mechanical APDL 时，您会看到以下打印结果，表明 Mechanical APDL 检测到了 Python UPF 指令并启动了一个 Python 服务器：

```
Processing "/upf" found in input file "my_inp.dat"

Python UPF Detected

PYTHON VERSION : 3.6
>>
>> START PYTHON GRPC SERVER
>>
>> User Functions Python File :  my_upf.py
>>
>> Server started on port [50054]
```

在 Mechanical APDL 进程中，您可以看到这个 Python 打印输出:

```
RUN SETUP PROCEDURE FROM FILE= /ansys_inc/v212/ansys/apdl/start.ans
=======================================
>> Inside the PYTHON UAnBeg routine  <<
=======================================
```

在这个过程的最后，Python 服务器会被自动关闭：

```
|-----------------------------------------------------------------|
|                                                                 |
|   CP Time      (sec) =          0.326       Time  =  10:40:24   |
|   Elapsed Time (sec) =          2.000       Date  =  03/11/2021 |
|                                                                 |
*-----------------------------------------------------------------*

>> We shutdown Python Server(s)
```


(heading113_3)=
## Accessing the database from the Python code

在您的UPF程序中，您可能需要以只读/可写模式访问 Mechanical APDL 数据库。

在 Python 代码中，你可以创建一个与 DB 服务器的连接。这个命令必须只调用一次，以便你可以根据静态变量的值来保护调用：

```python
import grpc
import sys
from mapdl import *

firstcall = 1


class MapdlUserService(MapdlUser_pb2_grpc.MapdlUserServiceServicer):
    #   ###############################################################
    def UserMat(self, request, context):
        global firstcall

        if firstcall == 1:
            print(">> Connection to the MAPDL DB Server\n")
            db.start()
            firstcall = 0

        # continuation of the python function
        # ...
```

一旦 DB 连接被初始化，您就可以在只读/可写模式访问 Mechaniacl APDL 实例的数据库。

在访问 Mechanical APDL 数据库所记录的函数中，有一个子集已被公开，因此可以从 Python 代码中调用它们。下表描述了这些公开的函数。

```{table} Supported database access functions

|   |   |
| --- | --- |
| `db.start()` | 初始化与一个正在运行的 Mechanical APDL 实例的连接。如果检测到带有 Python 文件的 **/UPF** 命令，DB 服务器将在 Mechanical APDL 中自动启动。|
| `db.stop()` | 关闭与 DB 服务器的连接。 |
| `db.ndnext(next)` | 等效于函数 `ndnext` 中描述的函数(获取下一个节点号) |
| `db.ndinqr(ind,key)` | 等效于函数 `ndinqr` 中描述的函数(获取关于节点的信息) |
| `db.getnod(inod)` | 等效于函数 `getnod` 中描述的函数(获取节点) |
| `db.putnod(inod,x,y,z)` | 等效于函数 `putnod` 中描述的函数(存储节点) |
| `db.elnext(ielm)` | 等效于函数 elnext 中描述的函数(获取下一个元素的编号) |
| `db.get_ElmInfo(inquire)` | 等效于访问求解和材料数据时描述的函数 `get_ElmInfo` |
| `db.get_ElmData(kchar, elemId, kMatRecPt, ncomp, vect)` | 等效于访问求解和材料数据时描述的函数 `get_ElmData` |
| ` db.putElmData(inquire, elemId, kIntg, nvect, vect)` | 等效于访问求解和材料数据时描述的函数 `put_ElmData` |
```


(heading113_4)=
## Python UPF limitations

Python UPF 功能有以下限制:
- 目前，不支持分布式 Ansys。您必须在命令行上指定 `-smp` 选项，以确保 Machical APDL 在共享内存处理模式下运行。
- Python UPF 只能在 **Linux** 平台上使用。


(heading113_5)=
## Python UPF examples
下面的 Python UPF 示例可以在 [UPF in PyMAPDL](https://mapdl.docs.pyansys.com/version/stable/examples/extended_examples/Python_UPF/python_upf_examples.html#python-upf-examples) 中找到:

- Python *UserMat* subroutine
- Python *UsrShift* subroutine
- Python *UserHyper* subroutine
