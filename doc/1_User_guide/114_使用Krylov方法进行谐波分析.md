# 使用Krylov方法进行谐波分析

## 简介
你可以使用基于频率扫描的 Krylov 方法，在声学或单场结构分析中对强迫频率模拟进行高性能的求解计算。

与全谐波分析类似，扫频 Krylov 方法使用全系统矩阵来计算谐波响应。完整的方法是在频率范围内的每个频率点进行求解，而扫频 Krylov 方法执行以下步骤来近似整个频率范围内的响应：

- 在请求的频率范围中间的频率值处建立一个 Krylov 子空间的向量集
- 减少了整个频率范围内的系统矩阵和负载
- Solves the reduced system
- 将结果向后扩展以计算谐波响应

Mecnanical APDL 提供了以下方式来实现使用 Krylov 方法的谐波分析：
1. Mechanical APDL commands
2. Mechanical APDL的*结构分析指南*中[通过 Krylov 方法进行的频率扫描谐波分析](https://ansyshelp.ansys.com/account/secured?returnurl=/Views/Secured/corp/v222/en/ans_str/str_Krysweep.html)中描述的APDL宏

### 假设
在使用 Krylov PyMAPDL 方法进行求解计算时，作出了以下假设:

- 假设刚度、质量和阻尼矩阵是常数(与频率无关)。
- 外部负载矢量在频率上是线性斜率的。斜率假设建立 Krylov 子空间的频率是在频率范围的中间。如果你想应用阶梯负载，有一个选项可以在 **`KrylovSolver.solve()`** 方法的输入中指定。

## PyMAPDL 中 Krylov 方法的实现
Krylov 方法的 PyMAPDL 实现为您提供了更高的定制化和灵活性，因为您可以使用 Python 编码的用户自定义子程序来访问子空间向量和简化求解。

如果您不需要定制，您可以使用 Mechanical APDL 命令，用 Krylov 方法解决谐波分析。更多信息，包括该方法背后的理论，请参见 Mechanical APDL 的结构分析指南中的 [通过 Krylov 方法的扫频谐波分析](https://ansyshelp.ansys.com/account/secured?returnurl=/Views/Secured/corp/v222/en/ans_str/str_Krysweep.html)。

有关 Krylov 方法的其他理论信息和方程，请参阅 Puri [^1]和 Eser [^2]的著作。

[^1]:Puri, S. R. (2009). Krylov Subspace Based Direct Projection Techniques for Low Frequency, Fully Coupled, Structural Acoustic Analysis and Optimization. PhD Thesis. Oxford Brookes University, Mechanical Engineering Department. Oxford, UK.
[^2]:Eser, M. C. (2019) Efficient Evaluation of Sound Radiation of an Electric Motor using Model Order Reduction. MSc Thesis. Technical University of Munich, Mechanical Engineering Department. Munich, DE.

PyMAPDL 中 exposure 遵循与 Mechanical APDL 宏相同的理论，有以下方法：

- **`KrylovSolver.gensubspace()`**: Creates the Krylov subspace.
- **`KrylovSolver.solve()`**: Solves the reduced system of equations.
- **`KrylovSolver.expand()`**: Expands the Krylov subspace.

```{warning}
这些方法必须连续运行。
```

## 用法
本节展示了如何实现与 Mechanical APDL 宏定义相同的分析。

### 生成 FULL 文件和 FEA 模型
使用 Mechanical APDL 为 Krylov 方法和 FEA 模型生成 FULL文件：

```python
  >>> from ansys.mapdl.core import launch_mapdl

  >>> mapdl = launch_mapdl()
  >>> mapdl.prep7()

      # Generate the FEA model (mesh, constraints, loads)
# ...

  >>> mapdl.run("/SOLU")
  >>> mapdl.antype("HARMIC")  # HARMONIC ANALYSIS
  >>> mapdl.hropt("KRYLOV")
  >>> mapdl.eqslv("SPARSE")
  >>> mapdl.harfrq(0,1000)  # Set beginning and ending frequency
  >>> mapdl.nsubst(100)  # Set the number of frequency increments
  >>> mapdl.wrfull(1)  # GENERATE .FULL FILE AND STOP
  >>> mapdl.solve()
  >>> mapdl.finish()
```

### 创建一个 Krylov 类的实例

```python
>>> mk = mapdl.krylov
```

调用 gensubspace 方法创建 Krylov 子空间，在 500Hz 的频率下建立一个大小/维度为 10 的子空间：

```python
>>> Qz = mk.gensubspace(10, 500, True)
```

### 返回 Krylov 子空间
调用 **`solve`** 方法来简化方程组并在每个频率下求解。下面这段代码求解了从 0 Hz到 1000 Hz 的问题，中间有 100 个间隔，分步加载：

```python
>>> Yz = mk.solve(0, 1000, 100, ramped_load=True)
```

### 在频率范围内返回缩减后的解
调用 **`expand`** 方法，将缩小后的解扩展到FE空间，输出扩展后的解，并计算残差：

```python
>>> result = mk.expand(
···    residual_computation=True, "L-inf", compute_solution_vectors=True, True
    )
···
```

如果 kwarg `out_key` 被设置为 `True`，则前面的代码会返回一个 **`numpy array`**。求解的向量会被映射到用户顺序。

```{note}
由 **`expand`** 方法返回的 **`numpy array`** 类包含每个计算频率的节点数和自由度(dof)解。
```

### 获得特定频率下 dof 的解

下面这段代码显示了如何在特定的频率或步长下得到节点解:

```python
# Get the nodal solution at freq number 3``````
>>> freq = 3
>>> nodal_sol = result[freq - 1]  # Get the nodal solution for each node
```

## Example
在 PyMAPDL 中使用 Krylov 方法的例子见 [《Harmonic analysis using the frequency-sweep Krylov method》](https://mapdl.docs.pyansys.com/version/stable/examples/extended_examples/Krylov/krylov_example.html#krylov-example)。

## 规定
若要在 PyMAPDL 中使用 Krylov 方法，必须使用 Machical APDL 2022 R2 或更高版本。

```{warning}
此特性不支持分布式 Ansys。但是，在启动 MachicalAPDL 时，您仍然可以在不指定 `-smp` 标志的情况下运行 Machical APDL Math 命令。
```
## Reference
关于 Krylov 方法的更多信息，请参见 Mechanical APDL *结构分析指南*中的 [通过Krylov方法的扫频谐波分析](https://ansyshelp.ansys.com/account/secured?returnurl=/Views/Secured/corp/v222/en/ans_str/str_Krysweep.html) 以及以下资源：


