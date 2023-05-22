# PyMAPDL 语法和用法
本页为您提供了 **`Mapdl`** class 的 PyMAPDL API 概述。更多信息请参见 [Mapdl module](https://mapdl.docs.pyansys.com/version/stable/api/mapdl.html#ref-mapdl-api)。

## Overview
当作为函数调用 MAPDL 命令时，每条命令都被从原来的 MAPDL 全 CAPS 格式翻译成(*MAPDL all CAPS format*) PEP8 兼容格式。例如，`ESEL` 现在是 **`Mapdl.esel()`** 方法。此外，含有 `/` 或 `*` 的 MAPDL 命令**已经删除了这些字符**，除非这会导致与现有名称的冲突。最值得注意的是 `/SOLU` ，它将与 `SOLU` 冲突。因此，`/SOLU` 被重新命名为 **`Mapdl.slashsolu()`** 方式，以区别于 `solu`。在 1500 条 MAPDL 命令中，约有15条以 `slash(/)` 开头，8 条以 `star(*)` 开头。

通常有一个空位的 MAPDL 命令，如 `ESEL,S,TYPE,,1`，在被 Python 调用时应包括一个 empty string (空字符串)：

```py
mapdl.esel("s", "type", "", 1)
```

或者，可以使用 keyword arguments (关键字参数调用)这些命令:

```py
mapdl.esel("s", "type", vmin=1)
```

这些限制都不适用于用 **`Mapdl.run()`** 方法运行的命令。运行其中的一些命令可能更容易，例如 `"/SOLU"` ：

```py
mapdl.run("/SOLU")
mapdl.solve()
```

你可以用另一种方法:

```py
mapdl.slashsolu()
```

有些命令只能在脚本中以非交互式方式运行。 PyMAPDL 通过将命令写入一个临时的输入文件，然后再读取该输入文件来绕过这一限制。要运行一组必须以非交互方式运行的命令，可以使用 **`Mapdl.non_interactive()`** 方法将 **`Mapdl`** class 设置为以输入文件方式运行一系列的命令。下面是一个例子：

```py
with mapdl.non_interactive:
    mapdl.run("*VWRITE,LABEL(1),VALUE(1,1),VALUE(1,2),VALUE(1,3)")
    mapdl.run("(1X,A8,'   ',F10.1,'  ',F10.1,'   ',1F5.3)")
```

注意，在 PyMAPDL 中创建的宏(而不是从文件加载的宏)似乎无法正确运行。例如，下面是使用 APDL 中的 `*CREATE` 命令创建的宏 `DISP`:

```
! SELECT NODES AT Z = 10 TO APPLY DISPLACEMENT
*CREATE,DISP
NSEL,R,LOC,Z,10
D,ALL,UZ,ARG1
NSEL,ALL
/OUT,SCRATCH
SOLVE
*END

! Call the function
*USE,DISP,-.032
*USE,DISP,-.05
*USE,DISP,-.1
```

它应该写成这样：

``` py
def DISP(
    ARG1="",
    ARG2="",
    ARG3="",
    ARG4="",
    ARG5="",
    ARG6="",
    ARG7="",
    ARG8="",
    ARG9="",
    ARG10="",
    ARG11="",
    ARG12="",
    ARG13="",
    ARG14="",
    ARG15="",
    ARG16="",
    ARG17="",
    ARG18="",
):
    mapdl.nsel("R", "LOC", "Z", 10)  # SELECT NODES AT Z = 10 TO APPLY DISPLACEMENT
    mapdl.d("ALL", "UZ", ARG1)
    mapdl.nsel("ALL")
    mapdl.run("/OUT,SCRATCH")
    mapdl.solve()


DISP(-0.032)
DISP(-0.05)
DISP(-0.1)
```

如果您有一个带有宏的现有输入文件，您可以使用 **`Convert_script()`** 方法进行转换，设置 "macros_as_function=True":

```py
>>> from ansys.mapdl import core as pymapdl
>>> pymapdl.convert_script(apdl_inputfile, pyscript, macros_as_functions=True)
```

### 运行 commands 时的其他选项
命令可以在 `mute`(静音)或 `verbose`(详细) 模式下运行，这允许您在任何 MAPDL 命令运行时禁止或打印输出。这对于像 `SOLVE` 这样需要长时间运行的命令特别有帮助,并且适用于所有命令的 Python 包装以及使用 **`Mapdl.run()`** 方法时。

运行命令并禁止其打印:

``` py
>>> mapdl.run("/PREP7", mute=True)

>>> mapdl.prep7(mute=True)
```

运行一个命令，并在运行过程中串流其输出：
```py
>>> mapdl.run("SOLVE", verbose=True)

>>> mapdl.solve(verbose=True)
```

```{note}
只有在 gRPC 模式下运行 MAPDL 时，`verbose` 和 `mute` 特性才可用。
```

### 运行多个命令或一个输入文件
可以使用 **`MAPDL.input_string()`** 方式作为一个 unified block 运行多个 MAPDL 命令。这在将 PyMAPDL 与旧的 MAPDL 脚本一起使用时非常有用。例如:

```py
cmd = """/prep7
! Mat
MP,EX,1,200000
MP,NUXY,1,0.3
MP,DENS,1,7.85e-09
! Elements
et,1,186
! Geometry
BLC4,0,0,1000,100,10
! Mesh
esize,5
vmesh,all"""
```

```py
>>> resp = mapdl.input_strings(cmd)
>>> resp
You have already entered the general preprocessor (PREP7).

MATERIAL          1     EX   =   200000.0

MATERIAL          1     NUXY =  0.3000000

MATERIAL          1     DENS =  0.7850000E-08

ELEMENT TYPE          1 IS SOLID186     3-D 20-NODE STRUCTURAL SOLID
KEYOPT( 1- 6)=        0      0      0        0      0      0
KEYOPT( 7-12)=        0      0      0        0      0      0
KEYOPT(13-18)=        0      0      0        0      0      0

CURRENT NODAL DOF SET IS  UX    UY    UZ
THREE-DIMENSIONAL MODEL

CREATE A HEXAHEDRAL VOLUME WITH
X-DISTANCES FROM      0.000000000     TO      1000.000000
Y-DISTANCES FROM      0.000000000     TO      100.0000000
Z-DISTANCES FROM      0.000000000     TO      10.00000000

    OUTPUT VOLUME =     1

DEFAULT ELEMENT DIVISIONS PER LINE BASED ON ELEMENT SIZE =   5.00

GENERATE NODES AND ELEMENTS   IN  ALL  SELECTED VOLUMES

NUMBER OF VOLUMES MESHED   =         1
MAXIMUM NODE NUMBER        =     45765
MAXIMUM ELEMENT NUMBER     =      8000
```

或者，您可以简单地将命令写入一个文件，然后使用 
 **`Mapdl.input()`** 方法运行该文件。例如，如果您有一个 `" ds.dat"` 文件，该文件是从 Ansys Machinery 生成的，那么您可以使用以下命令运行该文件:

```py
resp = mapdl.input("ds.dat")
```

### 条件语句和循环
诸如 `*IF` 的 APDL 条件语句必须以 Python 的方式实现，或者通过使用 **`Mapdl.non_interactive`** 属性。例如：

```{code-block} 
:caption: MAPDL 条件语句

*IF,ARG1,EQ,0,THEN
  *GET,ARG4,NX,ARG2     ! RETRIEVE COORDINATE LOCATIONS OF BOTH NODES
  *GET,ARG5,NY,ARG2
  *GET,ARG6,NZ,ARG2
  *GET,ARG7,NX,ARG3
  *GET,ARG8,NY,ARG3
  *GET,ARG9,NZ,ARG3
*ELSE
  *GET,ARG4,KX,ARG2     ! RETRIEVE COORDINATE LOCATIONS OF BOTH KEYPOINTS
  *GET,ARG5,KY,ARG2
  *GET,ARG6,KZ,ARG2
  *GET,ARG7,KX,ARG3
  *GET,ARG8,KY,ARG3
  *GET,ARG9,KZ,ARG3
*ENDIF
```

这应按以下方式实施：

```{code-block}
:class: python
:caption: 通过 mapdl.non_interactive 实现条件语句
with mapdl.non_interactive:
    mapdl.run("*IF,ARG1,EQ,0,THEN")
    mapdl.run("*GET,ARG4,NX,ARG2")  # RETRIEVE COORDINATE LOCATIONS OF BOTH NODES
    mapdl.run("*GET,ARG5,NY,ARG2")
    mapdl.run("*GET,ARG6,NZ,ARG2")
    mapdl.run("*GET,ARG7,NX,ARG3")
    mapdl.run("*GET,ARG8,NY,ARG3")
    mapdl.run("*GET,ARG9,NZ,ARG3")
    mapdl.run("*ELSE")
    mapdl.run("*GET,ARG4,KX,ARG2")  # RETRIEVE COORDINATE LOCATIONS OF BOTH KEYPOINTS
    mapdl.run("*GET,ARG5,KY,ARG2")
    mapdl.run("*GET,ARG6,KZ,ARG2")
    mapdl.run("*GET,ARG7,KX,ARG3")
    mapdl.run("*GET,ARG8,KY,ARG3")
    mapdl.run("*GET,ARG9,KZ,ARG3")
    mapdl.run("*ENDIF")
```

又或者,通过 Python 的实现方式如下:

```{code-block}
:caption: 通过 Python 实现条件语句

with mapdl.non_interactive:
    mapdl.run("*IF,ARG1,EQ,0,THEN")
    mapdl.run("*GET,ARG4,NX,ARG2")  # RETRIEVE COORDINATE LOCATIONS OF BOTH NODES
    mapdl.run("*GET,ARG5,NY,ARG2")
    mapdl.run("*GET,ARG6,NZ,ARG2")
    mapdl.run("*GET,ARG7,NX,ARG3")
    mapdl.run("*GET,ARG8,NY,ARG3")
    mapdl.run("*GET,ARG9,NZ,ARG3")
    mapdl.run("*ELSE")
    mapdl.run("*GET,ARG4,KX,ARG2")  # RETRIEVE COORDINATE LOCATIONS OF BOTH KEYPOINTS
    mapdl.run("*GET,ARG5,KY,ARG2")
    mapdl.run("*GET,ARG6,KZ,ARG2")
    mapdl.run("*GET,ARG7,KX,ARG3")
    mapdl.run("*GET,ARG8,KY,ARG3")
    mapdl.run("*GET,ARG9,KZ,ARG3")
    mapdl.run("*ENDIF")
```

使用 `*DO` 或 `*DOWHILE` 的 APDL 循环也应该使用 **`Mapdl.non_Interactive`** 属性实现，或者使用 Python 实现。

### Warnings and errors
Errors 是通过 Python 处理的，例如:

```py
try:
    mapdl.solve()
except:
    # do something else with MAPDL
    pass
```

在 MAPDL 中被忽略的命令被标记为错误。这与 MAPDL 的默认行为不同，在 MAPDL 中，被忽略的命令被当作警告处理。例如，在 `ansys-mapdl-core` 中，在错误的会话中运行一个命令会引发一个错误：

```py
>>> mapdl.finish()
>>> mapdl.k()

Exception:
K, , , ,

 *** WARNING ***                         CP =       0.307   TIME= 11:05:01
 K is not a recognized BEGIN command, abbreviation, or macro.  This
 command will be ignored.
```

你可以通过使用  **`Mapdl.ignore_errors()`** 函数来改变这种行为，使被忽略的命令可以被记录为警告，而不是作为异常提出。比如说：

```py
>>> mapdl.ignore_errors = True
>>> mapdl.k()  # warning silently ignored
```

### Prompts(提示)

来自 MAPDL 的提示会自动继续，就像 MAPDL 处于批处理模式一样。需要用户输入的命令，如 **`Mapdl.vwrite()`** 方法失败，必须以非交互式方式输入。

## APDL 命令日志
虽然 `ansys-mapdl-core` 的设计是为了通过使用 Python 调用 APDL 会话而使其更容易控制，但可能有必要使用 PyMAPDL 脚本生成的输入文件再次调用 MAPDL。这可以通过 `log_apdl='apdl.log'` 参数自动启用。启用这个参数会使 **`Mapdl`** class 将每条运行的命令写入活动的 **`Mapdl.directory`** 下的名为 `"apdl.log " `的日志文件中。例如：

```py
from ansys.mapdl.core import launch_mapdl

ansys = launch_mapdl(log_apdl="apdl.log")
ansys.prep7()
ansys.k(1, 0, 0, 0)
ansys.k(2, 1, 0, 0)
ansys.k(3, 1, 1, 0)
ansys.k(4, 0, 1, 0)
```

这段代码**将以下内容写入**  `"apdl.log" 文件:

```
/PREP7,
K,1,0,0,0
K,2,1,0,0
K,3,1,1,0
K,4,0,1,0
```

这允许将 Python 脚本转换为 APDL 脚本(条件语句、循环或函数除外)。

### 使用 `lgwrite` 方式
或者，如果只想要数据库命令输出，可以使用 **`Mapdl.lgwrite`**  方法将整个数据库命令日志写入文件。

## 交互式断点
在大多数情况下，打开 MAPDL GUI 是必要的或可选择的。**`Mapdl`** class 具有 **`Mapdl.open_gui()`** 方法，它允许你无缝地打开 GUI 而不丢失工作或不得不重新启动会话。比如说：

```{code-block}
:class: python
:lineno-start: 1
>>> from ansys.mapdl.core import launch_mapdl
>>> mapdl = launch_mapdl()
```

使用关键点创建一个正方形区域:

```{code-block} python
:lineno-start: 3
>>> mapdl.prep7()
>>> mapdl.k(1, 0, 0, 0)
>>> mapdl.k(2, 1, 0, 0)
>>> mapdl.k(3, 1, 1, 0)
>>> mapdl.k(4, 0, 1, 0)
>>> mapdl.l(1, 2)
>>> mapdl.l(2, 3)
>>> mapdl.l(3, 4)
>>> mapdl.l(4, 1)
>>> mapdl.al(1, 2, 3, 4)
```

打开 GUI:

```{code-block} python
:lineno-start: 13
>>> mapdl.open_gui()
```

然后继续你的工作:

```{code-block} python
:lineno-start: 14
>>> mapdl.et(1, "MESH200", 6)
>>> mapdl.amesh("all")
>>> mapdl.eplot()
```

这种方法避免了在交互式会话和脚本会话之间来回切换的麻烦。相反，您可以拥有一个脚本会话并从脚本会话打开一个 GUI，而不会丢失工作或进度。此外，GUI 中的任何更改都不会影响脚本。**您可以在 GUI 中进行试验，脚本不会受到影响。**

## 批处理

你可以定义一个运行 MAPDL 的函数，而不是通过调用 MAPDL 的输入文件来运行一个 MAPDL 批处理。下面这个例子是根据扭转载荷下的圆柱体的最大应力来进行一个网格收敛研究。

```{code-block} python
:lineno-start: 1
import numpy as np
from ansys.mapdl.core import launch_mapdl


def cylinder_batch(elemsize, plot=False):
    """报告一个悬臂支撑体的最大 von-mises 应力"""

    # clear
    mapdl.finish()
    mapdl.clear()

    # cylinder parameters
    radius = 2
    h_tip = 2
    height = 20
    force = 100 / radius
    pressure = force / (h_tip * 2 * np.pi * radius)

    mapdl.prep7()
    mapdl.et(1, 186)
    mapdl.et(2, 154)
    mapdl.r(1)
    mapdl.r(2)

    # Aluminum properties (or something)
    mapdl.mp("ex", 1, 10e6)
    mapdl.mp("nuxy", 1, 0.3)
    mapdl.mp("dens", 1, 0.1 / 386.1)
    mapdl.mp("dens", 2, 0)

    # Simple cylinder
    for i in range(4):
        mapdl.cylind(radius, "", "", height, 90 * (i - 1), 90 * i)

    mapdl.nummrg("kp")

    # mesh cylinder
    mapdl.lsel("s", "loc", "x", 0)
    mapdl.lsel("r", "loc", "y", 0)
    mapdl.lsel("r", "loc", "z", 0, height - h_tip)
    # mapdl.lesize('all', elemsize*2)
    mapdl.mshape(0)
    mapdl.mshkey(1)
    mapdl.esize(elemsize)
    mapdl.allsel("all")
    mapdl.vsweep("ALL")
    mapdl.csys(1)
    mapdl.asel("s", "loc", "z", "", height - h_tip + 0.0001)
    mapdl.asel("r", "loc", "x", radius)
    mapdl.local(11, 1)
    mapdl.csys(0)
    mapdl.aatt(2, 2, 2, 11)
    mapdl.amesh("all")
    mapdl.finish()

    if plot:
        mapdl.view(1, 1, 1, 1)
        mapdl.eplot()

    # new solution
    mapdl.slashsolu()
    mapdl.antype("static", "new")
    mapdl.eqslv("pcg", 1e-8)

    # Apply tangential pressure
    mapdl.esel("s", "type", "", 2)
    mapdl.sfe("all", 2, "pres", "", pressure)

    # Constrain bottom of cylinder/rod
    mapdl.asel("s", "loc", "z", 0)
    mapdl.nsla("s", 1)

    mapdl.d("all", "all")
    mapdl.allsel()
    mapdl.psf("pres", "", 2)
    mapdl.pbc("u", 1)
    mapdl.solve()
    mapdl.finish()

    # access results using MAPDL object
    result = mapdl.result

    # to access the results you could have run:
    # from ansys.mapdl import reader as pymapdl_reader
    # resultfile = os.path.join(mapdl.path, '%s.rst' % mapdl.jobname)
    # result = pymapdl_reader.read_binary(result file)

    # Get maximum von Mises stress at result 1
    # Index 0 as it's zero based indexing
    nodenum, stress = result.principal_nodal_stress(0)

    # von Mises stress is the last column
    # must be nanmax as the shell element stress is not recorded
    maxstress = np.nanmax(stress[:, -1])

    # return number of nodes and max stress
    return nodenum.size, maxstress


# initialize MAPDL
mapdl = launch_mapdl(override=True, loglevel="ERROR")

# call MAPDL to solve repeatedly
result_summ = []
for elemsize in np.linspace(0.6, 0.15, 15):
    # run the batch and report the results
    nnode, maxstress = cylinder_batch(elemsize, plot=False)
    result_summ.append([nnode, maxstress])
    print(
        "Element size %f: %6d nodes and maximum vom Mises stress %f"
        % (elemsize, nnode, maxstress)
    )

# Exit MAPDL
mapdl.exit()
```

下面是脚本的输出:

```
Element size 0.600000:   9657 nodes and maximum vom Mises stress 142.623505
Element size 0.567857:  10213 nodes and maximum vom Mises stress 142.697800
Element size 0.535714:  10769 nodes and maximum vom Mises stress 142.766510
Element size 0.503571:  14177 nodes and maximum vom Mises stress 142.585388
Element size 0.471429:  18371 nodes and maximum vom Mises stress 142.825684
Element size 0.439286:  19724 nodes and maximum vom Mises stress 142.841202
Element size 0.407143:  21412 nodes and maximum vom Mises stress 142.945984
Element size 0.375000:  33502 nodes and maximum vom Mises stress 142.913437
Element size 0.342857:  37877 nodes and maximum vom Mises stress 143.033401
Element size 0.310714:  59432 nodes and maximum vom Mises stress 143.328842
Element size 0.278571:  69106 nodes and maximum vom Mises stress 143.176086
Element size 0.246429: 110547 nodes and maximum vom Mises stress 143.499329
Element size 0.214286: 142496 nodes and maximum vom Mises stress 143.559128
Element size 0.182143: 211966 nodes and maximum vom Mises stress 143.953430
Element size 0.150000: 412324 nodes and maximum vom Mises stress 144.275406
```

## MAPDL 中的链式命令
MAPDL 通过使用分隔符 `"$"` 允许在一行上执行多个命令。可以在 PyMAPDL 中利用这一点，有效地将几个命令链接在一起，并将它们发送到 MAPDL 执行，而不是单独执行它们。当您需要在 Python 循环中执行成千上万个命令，并且不需要每个命令的单独结果时，链接命令会很有帮助。例如，如果你想沿着 X 轴创建1000个关键点，你可以运行:

```py
xloc = np.linspace(0, 1, 1000)
for x in xloc:
    mapdl.k(x=x)
```

但是，由于每个命令都是单独执行并返回响应，因此**分组发送**要由 MAPDL 执行的命令要快得多，并且 **`MAPDL`** class 通过使用 **`MAPDL.chain_command`** 属性对命令进行分组。

```{code-block} 
:emphasize-lines: 2
:class: python

xloc = np.linspace(0, 1, 1000)
with mapdl.chain_commands:  # 能快 4-10 倍
    for x in xloc:
        mapdl.k(x=x)
```

使用这种方法的执行时间通常比单独运行每个命令快4到10倍。然后，可以使用 **`Mapdl.last_response`** 属性查看链式命令的最终响应。

```{note}
分布式 MAPDL 不支持命令链接。若要提高性能，请使用 `mute=True` 或 **`Mapdl.non_interactive`** 属性。
```

## 向 MAPDL 发送数组
你可以使用 **`Mapdl.Parameters`** 属性直接向 MAPDL 发送 `numpy` 数组或 Python 列表。这比通过 Python 用 **`Mapdl.run()`** 方法单独向 MAPDL 发送参数要有效得多，因为它在后台使用了 **`Mapdl.vread()`** 方法。

```python
from ansys.mapdl.core import launch_mapdl
import numpy as np

mapdl = launch_mapdl()
arr = np.random.random((5, 3))
mapdl.parameters["MYARR"] = arr
```

通过对 **`Mapdl.Parameters`** 属性进行索引，验证数据是否已经正确加载到 MAPDL，就像 Python 字典一样：

```python
>>> array_from_mapdl = mapdl.parameters["MYARR"]
>>> array_from_mapdl
array([[0.65516567, 0.96977939, 0.3224993 ],
       [0.58634927, 0.84392263, 0.18152529],
       [0.76719759, 0.45748876, 0.56432361],
       [0.78548338, 0.01042177, 0.57420062],
       [0.33189362, 0.9681039 , 0.47525875]])
```

### 下载远程 MAPDL 文件
在 gRPC 模式下运行 MAPDL 时，可使用 **`Mapdl`** class 的 **`Mapdl.download()`** 函数列出和下载远程 MAPDL 文件。例如，下面的代码列出了远程文件并下载了其中一个文件：

``` python
remote_files = mapdl.list_files()

# ensure the result file is one of the remote files
assert "file.rst" in remote_files

# download the remote result file
mapdl.download("file.rst")
```

```{note}
这个特性只能在 MAPDL 2021R1 和更高版本中使用。
```

另外，你可以在 **`Mapdl.download()`*8 方法中使用 glob 模式或文件名列表，一次下载多个文件：
```py
# Using a list of file names
mapdl.download(["file0.log", "file1.out"])

# Using glob pattern to match the list_files
mapdl.download("file*")
```

你也可以使用这个函数下载 MAPDL 工作目录 (**`MAPDL.directory`**) 中的所有文件:
```py
mapdl.download_project()
```

或者，按扩展名进行过滤，如下例所示：
```py
mapdl.download_project(
    ["log", "out"], target_dir="myfiles"
)  # Download the files to 'myfiles' directory
```

### 上传本地 MAPDL 文件
您可以使用 **`MAPDL.load()`** 方法将本地 MAPDL 文件作为远程 MAPDL 实例上传:
```py
# upload a local file
mapdl.upload("sample.db")

# ensure the uploaded file is one of the remote files
remote_files = mapdl.list_files()
assert "sample.db" in remote_files
```

```{note}
这个特性只能在 MAPDL2021R1和更高版本中使用。
```

## 不受支持的 MAPDL 命令和其他注意事项
大多数 MAPDL 命令已经被 Python 映射到它们的等效方法中。然而，有些命令不被支持，因为它们要么不适用于交互式会话，要么需要额外的命令，而这些命令与 MAPDL 服务器上处理输入的方式不兼容。

### 无法使用的命令
由于各种原因，有些命令在 PyMAPDL 中不可用。

其中一些命令在 Python 上下文中是没有意义的，下面是一些例子:

- 可以用 Python `input` 替换 `*ASK` 命令。
- `*IF` 命令可以替换为 Python `if` 语句。
- `*CREATE` 和 `*USE` 命令可以用对另一个 Python 函数或模块的调用来替换。

其他命令在非 GUI 会话中没有意义。例如，在非 GUI 会话中不需要清除图形屏幕的 `/ERASE`  和 `ERASE` 命令。

其他命令被 `MAPDL` 悄悄地忽略了，但你仍然可以使用它们。例如，可以使用 **`mapdl.run("/BATCH")`** 方法运行 `/BATCH` 命令，它返回以下警告：

```
*** WARNING ***                         CP =       0.519   TIME= 12:04:16
The /BATCH command must be the first line of input.  The /BATCH command
is ignored.
```

{numref}`Non-available-commands` 是关于不可用的命令的综合信息

```{csv-table} 不可用的命令
:name: Non-available-commands
:header: >
: "", "MAPDL 命令", "Interactive", "Non-interactive", "Direct run", "Notes"

"**GUI 命令**", "- `*ASK`", "❌ Not available","❌ Not available", "✔️ Works", "当在 **`mapdl.run()`** 中使用时，它自动假定用户输入为 0，而使用 Python输入。"
" ", "- `*VEDIT`", "❌ Not available", "❌ Not available", "➖ MAPDL shows a warning", "它需要一个 GUI 会话才能工作。"
" ", "- `/EARSE`", "❌ Not available", "❌ Not available", "✔️ Works", "它在非 GUI 会话中没有意义。"
" ", "- `EARSE`", "❌ Not available", "❌ Not available", "➖ MAPDL shows a warning", "它在非 GUI 会话中没有意义。"
" ", "- `HELP`", "❌ Not available", "❌ Not available", "➖ Ignored by MAPDL", "它需要一个 GUI 会话才能工作。"
" ", "- `HELPDISP`", "❌ Not available", "❌ Not available", "➖ Ignored by MAPDL", "它需要一个 GUI 会话才能工作。"
" ", "- `NOERASE`", "❌ Not available", "❌ Not available", "✔️ Works", "它在非 GUI 会话中没有意义。"

"**控制流程命令**", "- `*CYCLE`", "❌ Not available","❌ Not available", "✔️ Works", "建议使用Python的控制流程关键字，在这种情况下是 `continue`。"
" ", "- `*DO`", "❌ Not available","❌ Not available", "✔️ Works", "建议使用Python的控制流程关键字，在这种情况下是 `for`。"
" ", "- `*DOWHILE`", "❌ Not available","❌ Not available", "✔️ Works", "建议使用Python的控制流程关键字，在这种情况下是 `WHILE`。"
" ", "- `*ELSE`", "❌ Not available","❌ Not available", "✔️ Works", "建议使用Python的控制流程关键字，在这种情况下是 `else`。"
" ", "- `*ELSEIF`", "❌ Not available","❌ Not available", "✔️ Works", "建议使用Python的控制流程关键字，在这种情况下是 `elif`。"
" ", "- `*ENDDO`", "❌ Not available","❌ Not available", "✔️ Works", "建议使用Python的控制流程关键字。"
" ", "- `*GO`", "❌ Not available","❌ Not available", "✔️ Works", "建议使用Python的控制流程关键字，如 `if` 或函数。"
" ", "- `*IF`", "❌ Not available","❌ Not available", "✔️ Works", "建议使用Python的控制流程关键字，在这种情况下是 `continue`。"
" ", "- `*REPEAT`", "❌ Not available","❌ Not available", "✔️ Works", "建议使用Python的控制流程关键字，如 `for` 或者 `while`。"
" ", "- `*RETURN`", "❌ Not available","❌ Not available", "✔️ Works", "建议使用Python的控制流程关键字，如 `break`、`continue` 或者 `return`。"

"**其他命令**", "- `*DEL`", "❌ Not available","❌ Not available", "✔️ Works", "建议使用 Python 变量(使用 Python 内存)而不是 MAPDL 变量。"
" ", "- `/BATCH`", "❌ Not available","❌ Not available", "➖ Ignored by MAPDL", "它在 PyMAPDL 会话中没有意义。"
" ", "- `/EOF`", "❌ Not available","❌ Not available", "❌ PyMAPDL shows an exception", "要停止服务器，请使用 **`mapdl.exit()`**"
" ", "- `UNDO`", "❌ Not available","❌ Not available", "➖ MAPDL shows a warning", "它不撤消任何命令。"
```

````{note}
- **Interactive** 意味着在 MAPDL 中存在一个方法，例如 **`Mapdl.prep7()`** 方法。
- **Non-interactive** 意味着他在 **`Mapdl.non_interactive`** context block、**`Mapdl.input()`** method 或 **`Madpdl.input_strings()`** method 中运行，例如：
    ``` py
    with mapdl.non_interactive:
        mapdl.prep7()
    ```
- **Direct run** 是指可以使用 **`mapdl.run()`** 方法来运行 MAPDL 命令。一个例子是 **`mapdl.run("/PREP7")`** 方法。
````

注意，用 **`mapdl.run()`** 方法运行这些命令不会导致MAPDL 退出。然而，它运行时可能会引发异常。

这些 MAPDL 命令也可以用 **`mapdl.input()`** 方法或 **`mapdl.input_strings()`** 方法执行。其结果应与在正常的批处理 MAPDL 会话中运行它们相同。



## 不受支持的“交互式”命令
以下命令只能在非交互式模式下运行（在 **`Mapdl.non_interactive`** 块内或使用 **`mapdl.input()`** 方法）。

{numref}`Non-interactive-only-commands`提供了关于不受支持的“交互式”命令的全面信息。

```{csv-table} 仅限于非交互式命令
:name: Non-interactive-only-commands
:header: >
: "", "Interative", "Non-Interactive", "Direct on", "Notes"

"- `*CREATE`", "❌ Not available", "✔️ Available", "➖ Only in **`Mapdl.non_interactive`**", "建议用创建 Python 函数来代替。"
"- `CFOPEN`", "❌ Not available", "✔️ Available", "➖ Only in **`Mapdl.non_interactive`**", "建议用创建 Python 函数，如 `open`。"
"- `CFCLOSE`", "❌ Not available", "✔️ Available", "➖ Only in **`Mapdl.non_interactive`**", "建议用创建 Python 函数，如 `open`。(这里是不是有问题?--ff)"
"- `*VWRITE`", "❌ Not available", "✔️ Available", "➖ Only in **`Mapdl.non_interactive`**", "如果你在一个本地会话中工作，建议你使用 Python 函数，如 `open`。(三个都是 'open'?--ff)"
"- `LSWRITE`", "✔️ Available (内部运行在 **`Mapdl.non_interactive`** 中)", "✔️ Available", "➖ Only in **`Mapdl.non_interactive`**", ""
```

## 环境变量
有几个特定于 PyMAPDL 的环境变量可以用来控制 PyMAPDL 和 MAPDL 的行为或启动，包括下表中所描述的那些变量。

% 写一个field list试试

| | |
|:---|:---|
|`ANSYSLMD_LICENSE_FILE`|  许可证文件或IP地址（192.168.0.16）。这对于为Docker提供许可是有帮助的。|
|`PYMAPDL_MAX_MESSAGE_LENGTH`|  最大的 gRPC 消息长度。如果你的连接在运行 PRNSOL 或 NLIST 时被终止，请提高这个值。以字节为单位，默认为 256MB。|
|`PYMAPDL_PORT`| 连接 PyMAPDL 时要查找的默认端口。通常用于单元测试。|
|`PYMAPDL_START_INSTANCE`|  覆盖 **`ansys.mapdl.core.launch_mapdl()`** 函数的行为，只尝试连接到 PyMAPDL 的现有实例。通常与 `PYMAPDL_PORT` 结合使用。|




