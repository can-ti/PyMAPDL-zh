# Solution

````{class} class ansys.mapdl.core.solution.Solution(mapdl)

Collection of parameters specific to the solution.

Useful for checking the status of a solve after running `mapdl.solve()` and determining if it converged, the number of iterations to converge, etc.\
用于在运行 `mapdl.solve()` 后检查求解状态，并确定是否收敛、收敛的迭代次数等。


Examples
--------

Check if a solution has converged.\
检查求解是否收敛。

```python
>>> mapdl.solution.converged
True
```

Get the cumulative number of iterations.\
获取累计迭代次数。

```python
>>> mapdl.solution.n_cmit
1.0
```

Methods
---------


Attributes
-----------

```{table}

| | | |
|---|---|---|
| {doc}`Solution.converged <../Solution/converged>` | Convergence indicator. | 收敛时为 `True`。 |
| {doc}`Solution.current_cnv <../Solution/current_cnv>` | Current convergence value. | 当前收敛值。 |
| {doc}`Solution.current_segment_cnv <../Solution/current_segment_cnv>` | Current segment convergence value. | 当前分段收敛值 |
| {doc}`Solution.decent_parm <../Solution/decent_parm>` | Descent parameter. |  |
| {doc}`Solution.displacement_cnv <../Solution/displacement_cnv>` | Displacement convergence value. | 位移收敛值 |
| {doc}`Solution.fluid_flow_cnv <../Solution/fluid_flow_cnv>` | Fluid flow convergence value. | 流体流量收敛值 |
| {doc}`Solution.force_cnv <../Solution/force_cnv>` | Force convergence value. | 力收敛值 |
| {doc}`Solution.heat_flow_cnv <../Solution/heat_flow_cnv>` | Heat flow convergence value. | 热流收敛值 |
| {doc}`Solution.magnetic_flux_cnv <../Solution/magnetic_flux_cnv>` | Magnetic flux convergence value. | 磁通量收敛值 |
| {doc}`Solution.moment_cnv <../Solution/moment_cnv>` | Moment convergence value. | 弯矩收敛值 |
| {doc}`Solution.mx_creep_rat <../Solution/mx_creep_rat>` | Maximum creep ratio. | 最大蠕变率 |
| {doc}`Solution.mx_dof <../Solution/mx_dof>` | Maximum degree of freedom value. | 最大自由度值 |
| {doc}`Solution.mx_plastic_inc <../Solution/mx_plastic_inc>` | Maximum plastic strain increment. | 最大塑性应变增量 |
| {doc}`Solution.n_cg_iter <../Solution/n_cg_iter>` | Number of iterations in the PCG and symmetric JCG (non-complex version) solvers. | PCG 和对称 JCG（非复杂版本）求解器的迭代次数 |
| {doc}`Solution.n_cmit <../Solution/n_cmit>` | Cumulative number of iterations. | 累计迭代次数 |
| {doc}`Solution.n_cmls <../Solution/n_cmls>` | Cumulative number of load steps. | 累计加载步数 |
| {doc}`Solution.n_cmss <../Solution/n_cmss>` | Number of substeps. | 子步数 |
| {doc}`Solution.n_eqit <../Solution/n_eqit>` | Number of equilibrium iterations. | 平衡迭代次数 |
| {doc}`Solution.pressure_conv <../Solution/pressure_conv>` | Pressure convergence value. | 压力收敛值。 |
| {doc}`Solution.res_eig <../Solution/res_eig>` | Response eigenvalue for 1st order systems. | 一阶系统的响应特征值 |
| {doc}`Solution.res_frq <../Solution/res_frq>` | Response frequency for 2nd order systems. | 二阶系统的响应频率 |
| {doc}`Solution.rotation_cnv <../Solution/rotation_cnv>` | Rotation convergence value. | 旋转收敛值 |
| {doc}`Solution.smcv <../Solution/smcv>` | Scalar magnetic potential convergence value. | 标量磁势收敛值 |
| {doc}`Solution.temperature_cnv <../Solution/temperature_cnv>` | Temperature convergence value. | 温度收敛值 |
| {doc}`Solution.time_step_size <../Solution/time_step_size>` | Time step size. | 时间步长 |
| {doc}`Solution.vector_cnv <../Solution/vector_cnv>` | Vector magnetic potential convergence value. | 矢量磁势收敛值 |
| {doc}`Solution.velocity_conv <../Solution/velocity_conv>` | Velocity convergence value. | 速度收敛值 |
| {doc}`Solution.voltage_conv <../Solution/voltage_conv>` | Voltage convergence value. | 电压收敛值 |

```



````