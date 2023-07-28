# KrylovSolver

````{class} ansys.mapdl.core.krylov.KrylovSolver(mapdl)

Abstract mapdl krylov class. Created from a `Mapdl` instance.\
KrylovSolver————一个稀疏矩阵求解器，子空闲迭代法。

Notes
-------

The procedure to use the Krylov solver is composed of three steps:\
使用 Krylov(克雷洛夫) 求解器的程序包括三个步骤：

1. Generate Krylov subspace using `KrylovSolver.gensubspace`.\
使用 `KrylovSolver.gensubspace` 生成克雷洛夫子空间。

2. Use `KrylovSolver.solve` to solve the generated Krylovsub space using a reduced harmonic analysis over a specified frequency range\
使用 "KrylovSolver.solve"，在指定频率范围内使用还原谐波分析求解生成的 Krylovsub 空间

3. Expand the reduced solution back to the original space using `KrylovSolver.solve`\
使用 `KrylovSolver.solve` 将缩小后的解扩展回原始空间

Examples
----------

Create an instance.

```python
>>> from ansys.mapdl.core import launch_mapdl
>>> mapdl = launch_mapdl()
>>> ....
>>> ....
>>> Generate the FEA model (mesh, constraints, loads)
>>> Generate the .full file
```

```python
>>> mk = mapdl.krylov
>>> # Generate the Krylov subspace
>>> Qz = mk.gensubspace(10, 100, check_orthogonality=True)
>>> # Reduce the system of equations and solve at each frequency.
>>> Yz = mk.solve(10, 100,  freq_steps=1, ramped_load=True)
>>> # Expand the reduced solution back to the FE space.
>>> res = mk.expand(residual_computation=True, residual_algorithm="l2")
```

Methods
-------

```{table}

| | | |
|---|---|---|
| {doc}`KrylovSolver.compute_residuals(iFreq, RzV, ...)  <../306_`KrylovSolver`_module/KrylovSolver/compute_residuals>`  | Compute residuals of the matrices. | 计算矩阵的残差。 |
| {doc}`KrylovSolver.expand([residual_computation, ...]) <../306_`KrylovSolver`_module/KrylovSolver/expand>`  | Expand the reduced solution back to FE space. | 将缩减后的解扩展回 FE 空间。 |
| {doc}`KrylovSolver.gensubspace(max_dim_q, frequency)   <../306_`KrylovSolver`_module/KrylovSolver/gensubspace>`  | Generate a Krylov subspace for model reduction in a harmonic analysis. | 为谐波分析中的模型还原生成一个克雷洛夫子空间。 |
| {doc}`KrylovSolver.solve(freq_start, freq_end, ...)    <../306_`KrylovSolver`_module/KrylovSolver/solve>`  | Reduce the system of equations and solve at each frequency. | 还原方程组，并在每个频率上求解。 |

```

Attributes
---------

```{table}

| | | |
|---|---|---|
| {doc}`KrylovSolver.is_orthogonal  <../306_`KrylovSolver`_module/KrylovSolver/is_orthogonal>`  | Check whether the solution is orthogonal. | 检查解是否正交。 |

```

````