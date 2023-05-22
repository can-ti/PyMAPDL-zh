# APDL Math 概述
APDL Math 提供了访问和操作大型稀疏矩阵的能力，并解决各种特征问题。PyMAPDL classes 和绑定以类似于流行的 numpy 和 scipy 库的方式呈现 APDL Math。APDL Math 命令集基于操作大型数学矩阵和向量的工具，这些工具提供了对标准线性代数操作的访问，对ANSYS Mechanical APDL（MAPDL）的强大稀疏线性求解器的访问，以及解决特征问题的能力。

Python 和 MATLAB 的 eigensolvers(特征求解器) 是基于开源的 LAPACK 库，可以为相对较小自由度（dof）的特征问题(大概 100,000 个自由度)提供合理的解决时间。然而，Ansys 求解器是为 100s 的百万自由度规模而设计的，你可以在各种特征问题上直接利用 Ansys 高性能求解器。幸运的是，您不需要重新学习一门全新的语言就可以利用这一点，因为 APDL Math是以类似于 `numpy` 和 `scipy` 库的方式编写的。例如，这里是 NumPy 和 SciPy 线性代数求解器与 Ansys MAPDL Math 求解器的对比：


% 写下面这个表格的时候,标题中不能出现反引号`,会报错,但代码块可以嵌套进表内
````{csv-table} numpy vs Pymapdl Math Implementation
:align: center
:header: > 
: "`numpy` and `scipy`", "`ansys.mapdl.math`"

"```python
k_py = k + sparse.triu(k, 1).T
m_py = m + sparse.triu(m, 1).T
n = 10
ev = linalg.eigsh(k_py, k=neqv, M=m_py)
```", "```python
k = mm.matrix(k_py, triu=True)
m = mm.matrix(m_py, triu=True)
n = 10
ev = mm.eigs(n, k, m)
```"
````

下面是一个基本的例子和对 PyMAPDL math API 的详细描述。关于其他的 PyMAPDL Math 示例，请参阅 [PyMAPDL math examples](https://mapdl.docs.pyansys.com/version/stable/examples/gallery_examples/01-apdlmath-examples/index.html#ref-apdl-math-examples)。

## MAPDL matrix 示例
这个例子演示了如何将 MAPDL math 矩阵从 MAPDL 发送到 Python，然后将其发送回去求解。虽然这个例子运行的是 MAPDL 生成的质量和刚度矩阵的 **`MapdlMath.eig()`** 方法，但是你可以使用外部 FEM 工具生成的质量和刚度矩阵，甚至可以在 Python 中修改质量和刚度矩阵。

首先，用 MAPDL 求解`1 × 1 × 1` 钢立方体的前 10 阶模态。

```python
import re

from ansys.mapdl.core import launch_mapdl

mapdl = launch_mapdl()

# setup the full file
mapdl.prep7()
mapdl.block(0, 1, 0, 1, 0, 1)
mapdl.et(1, 186)
mapdl.esize(0.5)
mapdl.vmesh("all")

# Define a material (nominal steel in SI)
mapdl.mp("EX", 1, 210e9)  # Elastic moduli in Pa (kg/(m*s**2))
mapdl.mp("DENS", 1, 7800)  # Density in kg/m3
mapdl.mp("NUXY", 1, 0.3)  # Poisson's Ratio

# solve first 10 non-trivial modes
out = mapdl.modal_analysis(nmode=10, freqb=1)

# store the first 10 natural frequencies
mapdl.post1()
resp = mapdl.set("LIST")
w_n = np.array(re.findall(r"\s\d*\.\d\s", resp), np.float32)
print(w_n)
```

现在你已经解出了立方体的前 10 阶模态:

```
[1475.1 1475.1 2018.8 2018.8 2018.8 2024.8 2024.8 2024.8 2242.2 2274.8]
```

接下来，加载默认存储在 `<jobname>.full` 文件中的质量和刚度矩阵。首先，创建一个 **`MapdlMath`** 类的实例为 `mm`：

```python
mm = mapdl.math

# load by default from file.full
k = mm.stiff()
m = mm.mass()

# convert to numpy
k_py = k.asarray()
m_py = m.asarray()
mapdl.clear()
print(k_py)
```

在运行 **`Mapdl.clear()`** 方法之后，这些矩阵将仅单独存储在 Python 中。
```
(0, 0)      37019230769.223404
(0, 1)      10283119658.117708
(0, 2)      10283119658.117706
:   :
(240, 241)  11217948717.943113
(241, 241)  50854700854.68495
(242, 242)  95726495726.47179
```

最后一步是将这些矩阵送回 MAPDL 进行求解。在你 'clear' MAPDL 的同时，你可以关闭 MAPDL，甚至可以把矩阵转移到另一个 MAPDL 会话中去求解：

```python
my_stiff = mm.matrix(k_py, triu=True)
my_mass = mm.matrix(m_py, triu=True)

# solve for the first 10 modes above 1 Hz
nmode = 10
mapdl_vec = mm.eigs(nmode, my_stiff, my_mass, fmin=1)
eigval = mapdl_vec.asarray()
print(eigval)
```

正如预期的那样，从 **`MapdlMath.eigs()`** 方法中得到的自然频率与 MAPDL 中 **`Mapdl.solve()`** 方法的结果是相同的。

```
[1475.1333421  1475.1333426  2018.83737064 2018.83737109 2018.83737237
 2024.78684466 2024.78684561 2024.7868466  2242.21532585 2274.82997741]
```

如果你想获得特征向量以及特征值，请初始化一个矩阵 `eigvec` 并将其发送到 **`MapdlMath.eigs()`** 方法：

```python
>>> nmode = 10
>>> eigvec = mm.zeros(my_stiff.nrow, nmode)  # for eigenvectors
>>> val = mm.eigs(nmode, my_stiff, my_mass, fmin=1)
```

MAPDL Math 矩阵 `eigvec` 现在包含解的特征向量。

## APDL Math reference
有关更多信息，请参见 [MapdlMath module](https://mapdl.docs.pyansys.com/version/stable/api/math.html#ref-math-api)。

