# Julia 和 PyMAPDL
如果你喜欢与 Julia 一起工作，你可以使用 Python 库，就像它们是 Julia 包一样。

## 安装 Julia
要安装 [Julia](https://julialang.org/)，请访问他们的网站，并按照下载部分给出的说明进行操作。
- [Windows](https://julialang.org/downloads/platform/#windows)
- [Linus](https://julialang.org/downloads/platform/#linux_and_freebsd)
- [MacOS](https://julialang.org/downloads/platform/#macos)

## 设置 Julia 环境
要访问 Julia 中的 Python 库，必须安装 [PyCall](https://github.com/JuliaPy/PyCall.jl) Julia 包。要安装它，运行 Julia 并按下 `"]"` 键切换到包管理器。

如果你需要使用不同的软件包版本或应用程序，在 Julia 中创建一个虚拟环境是很有用的。要创建一个虚拟环境，请使用 `activate` 命令，输入你要创建或激活的新环境的名称。

``` 
pkg> activate julia_test
  Activating project at `C:/Users/USER/julia_test`
```

这时应该会出现一条信息，表明新的软件包（`julia_test`）已经被激活。此环境名称现在位于命令行之前。

``` 
(julia_test) pkg>
```

接下来输入:

``` 
(julia_test) pkg> add PyCall
```

要使用 PyCall，按退格键进入 Julia 命令行。然后，命令行前面会有 `Julia` 这个名字。

``` 
julia>
```

接下来使用 PyCall 包:

```
 julia> using PyCall
```

这应该足以使用 Python 基础发行版中所包含的包。

例如:

``` 
julia> math = pyimport("math")
math.sin(math.pi/4) # returns ≈ 1/√2 = 0.70710678..
```

## 在 Julia 中安装 PyMAPDL
PyCall 包括一个轻量级的 Python 环境，它使用 [Conda](https://conda.io/) 来管理和访问 Python 包。这个环境，目前基于 Python 3.9.7，包括标准的基本 Python 库。但是，因为它是一个完全可以工作的 Python 环境，因此你仍然可以在 Julia 命令行之外使用它，并使用 `pip` 安装 Python 包。

要安装 PyMAPDL，首先使用以下命令定位 Python 可执行文件:

```
julia> PyCall.python
"C:\\Users\\USER\\.julia\\conda\\3\\python.exe"
```

在 Linux 中，前面的代码会打印出以下内容，其中 `python3` 是操作系统的默认 Python3 安装。

```
julia> PyCall.python
"python3"
```

```{note}
在 Linux 中，没有特定的安装步骤。您只需要将 Julia 的可执行文件添加到路径中。因此，Julia 的 Python 安装路径可能因用户而异。例如，如果您解压了 `/home/USER/Julia` 中的源文件，那么 Julia 的路径就是 `/home/USER/Julia/Julia-1.7.2/bin`。
```

你将使用这个 Python 可执行文件来安装 PyMAPDL：

``` 
C:\Users\USER\.julia\conda\3\python.exe -m pip install ansys-mapdl-core
```

在 Linux 中,您可以通过下面方式进行安装:

```
python3 -m pip install ansys-mapdl-core
```

最后，在重新启动 Julia 之后，您就可以使用前面描述的相同过程导入 PyMAPDL:

```
julia> using PyCall
julia> pymapdl = pyimport("ansys.mapdl.core")
PyObject <module 'ansys.mapdl.core' from 'C:\\Users\\USER\\.julia\\conda\\3\\lib\\site-packages\\ansys\\mapdl\\core\\__init__.py'>
julia> mapdl = pymapdl.launch_mapdl()
julia> print(mapdl.__str__())
Product:             Ansys Mechanical Enterprise
MAPDL Version:       21.2
ansys.mapdl Version: 0.60.6
```

````{note}
如果在使用 PyCall 时遇到错误，您可以尝试通过按下 `"]"` 来重新构建包，然后进入包管理器并输入:
```
pkg> build PyCall
```
````

## 在 Julia 中使用 PyMAPDL
下面是在 Julia 中使用 PyMAPDL 的一个简单示例:

```julia
using PyCall
pymapdl = pyimport("ansys.mapdl.core")
mapdl = pymapdl.launch_mapdl()
np = pyimport("numpy")
# define cylinder and mesh parameters
torque = 100
radius = 2
h_tip = 2
height = 20
elemsize = 0.5
pi = np.arccos(-1)
force = 100/radius
pressure = force/(h_tip*2*np.pi*radius)
# Define higher-order SOLID186
# Define surface effect elements SURF154 to apply torque
# as a tangential pressure
mapdl.prep7()
mapdl.et(1, 186)
mapdl.et(2, 154)
mapdl.r(1)
mapdl.r(2)
# Aluminum properties (or something)
mapdl.mp("ex", 1, 10e6)
mapdl.mp("nuxy", 1, 0.3)
mapdl.mp("dens", 1, 0.1/386.1)
mapdl.mp("dens", 2, 0)
# Simple cylinder
for i in 1:5
    mapdl.cylind(radius, "", "", height, 90*(i-1), 90*i)
end
mapdl.nummrg("kp")
# interactive volume plot (optional)
mapdl.vplot()
# mesh cylinder
mapdl.lsel("s", "loc", "x", 0)
mapdl.lsel("r", "loc", "y", 0)
mapdl.lsel("r", "loc", "z", 0, height - h_tip)
mapdl.lesize("all", elemsize*2)
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
# plot elements
mapdl.eplot()
```

```{note}
注意字符串和循环中的变化。只允许`""`字符串。
```










