# modal_analysis

````{method} Mapdl.modal_analysis(method='lanb', nmode='', freqb='', freqe='', cpxmod='', nrmkey='', modtype='', memory_option='', mxpand='', elcalc=False)

Run a modal with basic settings analysis.(`*MODOPT`)\
运行模态，进行基本设置分析。(`*MODOPT`)


Parameters:
----------

  method : *`str`*
  : Mode-extraction method to be used for the modal analysis. Defaults to lanb (block lanczos). Must be one of the following:\
  用于模态分析的模态提取方法。默认为 `'LANB'`（block lanczos）。必须是以下选项之一：
  - LANB : Block Lanczos
  - LANPCG : PCG Lanczos
  - SNODE : Supernode modal solver - 超节点模态求解器
  - SUBSP : Subspace algorithm - 子空间算法
  - UNSYM : Unsymmetric matrix - 非对称矩阵
  - DAMP : Damped system - 阻尼系统
  - QRDAMP : Damped system using QR algorithm
  - VT : Variational Technology - 变分法

  nmode : *`int`* , *`optional`*
  : The number of modes to extract. The value can depend on the value supplied for `Method`. NMODE has no default and must be specified. If Method = LANB, LANPCG, or SNODE, the number of modes that can be extracted can equal the DOFs in the model after the application of all boundary conditions.\
  要提取的模态阶数。该值取决于为 `Method` 提供的值。NMODE 没有默认值，必须指定。如果 Method = LANB、LANPCG 或 SNODE，可提取的模态数可能等于应用所有边界条件后模型中的 DOF。

  freqb : *`float`* , *`optional`*
  : The beginning, or lower end, of the frequency range (or eigenvalue range if `'FREQMOD'` is specified) of interest.\
  感兴趣的频率范围（或特征值范围，如果指定了 `'FREQMOD'`）的起点或下限。\
  For Method = LANB, SUBSP, UNSYM, DAMP, and QRDAMP, FREQB also represents the first shift point for the eigenvalue iterations. For UNSYM and DAMP, the default = -1.0 For other methods, the default is calculated internally.\
  对于 Method = LANB、SUBSP、UNSYM、DAMP 和 QRDAMP，FREQB 还表示特征值迭代的第一个移动点。对于 UNSYM 和 DAMP，默认值 = -1.0 对于其他方法，默认值由内部计算得出。\
  Eigenvalue extraction is most accurate near the shift point. Multiple shift points are used internally in the LANB, SUBSP, UNSYM, and QRDAMP methods. For the LANB, LANPCG, SUBSP, UNSYM, DAMP, and QRDAMP methods with a positive FREQB value, eigenvalues are output beginning at the shift point and increase in magnitude. For the UNSYM and DAMP methods with a negative FREQB value, eigenvalues are output beginning at zero magnitude and increase.\
  特征值提取在移位点附近最为精确。LANB、SUBSP、UNSYM 和 QRDAMP 方法内部使用多个移位点。对于具有正 FREQB 值的 LANB、LANPCG、SUBSP、UNSYM、DAMP 和 QRDAMP 方法，特征值从偏移点开始输出，并逐渐增大。对于具有负 FREQB 值的 UNSYM 和 DAMP 方法，特征值从零幅度开始输出并增加。\
  Choosing higher FREQB values with the LANPCG and SNODE methods may lead to inefficient solution times because these methods will find all eigenvalues between zero and FREQB before finding the requested modes between FREQB and FREQE.\
  使用 LANPCG 和 SNODE 方法选择较高的 FREQB 值可能会导致求解时间效率低下，因为这些方法在找到 FREQB 和 FREQE 之间的所需模式之前，会先找到零和 FREQB 之间的所有特征值。

  freqe : *`float`* , *`optional`*
  : The ending, or upper end, of the frequency range of interest (in Hz). The default for `Method = 'SNODE'` is described below. The default for all other methods is to calculate all modes, regardless of their maximum frequency.\
  相关频率范围的终点或上限（单位 Hz）。`Method = 'SNODE'` 的默认值如下所述。所有其他方法的默认值是计算所有模式，无论其最大频率如何。\
  To maintain solution efficiency, do not set the FREQE value too high; for example, not higher than 5000 Hz for an industrial problem. The higher the FREQE value used for the SNODE method, the more accurate the solution and the more eigenvalues produced; however, the solution time also increases. For example, if FREQE is set to 1e8, it causes the underlying supernodal structures to find all possible eigenvalues of each group of supernodes, requiring excessive solution time. The accuracy of the SNODE solution is controlled by FREQE and by the RangeFact value on the SNOPTION command.\
  为保持求解效率，请勿将 FREQE 值设得过高；例如，工业问题的 FREQE 值不得高于 5000 Hz。SNODE 方法使用的 FREQE 值越高，解法越精确，产生的特征值越多；但是，解法时间也会增加。例如，如果将 FREQE 设为 1e8，就会导致底层超节点结构寻找每组超节点的所有可能特征值，从而耗费过多的求解时间。SNODE 求解的精度由 FREQE 和 SNOPTION 命令中的 RangeFact 值控制。

  cpxmod : *`str`* , *`optional`*
  : Complex eigenmode key. Valid only when `method='QRDAMP'` or `method='unsym'`.\
  复杂特征模态键。仅当 `method='QRDAMP'` 或 `method='unsym'` 时有效。
  - AUTO : Determine automatically if the eigensolutions are real or complex and output them accordingly. This is the default for `method='UNSYM'`. Not supported for `Method = 'QRDAMP'`.\
  AUTO：自动判断等效解是实数还是复数，并据此输出。这是 `method='UNSYM'`的默认设置。不支持 `Method = 'QRDAMP'`。
  - ON or CPLX : Calculate and output complex eigenmode shapes.\
  ON 或 CPLX：计算并输出复特征模态振形。
  - OFF or REAL : Do not calculate complex eigenmode shapes. This is required if a mode-superposition analysis is intended after the modal analysis for `Method = 'QRDAMP'`. This is the default for this method.\
  OFF 或 REAL：不计算复特征模态振型。如果要在 `Method = 'QRDAMP'` 的模态分析后进行模态叠加分析，则需要执行此操作。这是此方法的默认设置。

  nrmkey : *`bool`* , *`optional`*
  : Mode shape normalization key. When `True` (default), normalize the mode shapes to the mass matrix. When `False`, Normalize the mode shapes to unity instead of to the mass matrix. If a subsequent spectrum or mode-superposition analysis is planned, the mode shapes should be normalized to the mass matrix.\
  模态振型归一化键。当 `True`（默认值）时，将模态振型归一化为质量矩阵。当 `False`（假）时，将模态振型归一化为统一值，而不是质量矩阵。如果计划随后进行谱分析或模态叠加分析，则应将模态振型归一化为质量矩阵。

  modtype : *`str`* , *`optional`*
  : Type of modes calculated by the eigensolver. Only applicable to the unsymmetric eigensolver.\
  特征分解器计算的模式类型。仅适用于非对称求解器。
  - Blank : Right eigenmodes. This value is the default.\
  Blank ：右特征值。该值为默认值。
  - BOTH : Right and left eigenmodes. The left eigenmodes are written to Jobname.LMODE. This option must be activated if a mode-superposition analysis is intended.\
  BOTH : 左右特征模态。左特征模态将写入 Jobname.LMODE。如果要进行模态叠加分析，则必须激活该选项。

  memory_option : *`str`* , *`optional`*
  : Memory allocation option: 内存分配选项：
  - `DEFAULT` - Default Memory mode (默认内存模式)\
  Use the default memory allocation strategy for the sparse solver. The default strategy attempts to run in the `INCORE` memory mode. If there is not enough available physical memory when the solver starts to run in the `INCORE` memory mode, the solver will then attempt to run in the `OUTOFCORE` memory mode.\
  使用稀疏求解器的默认内存分配策略。默认策略会尝试在 "INCORE "内存模式下运行。如果求解器在 "INCORE "内存模式下开始运行时没有足够的可用物理内存，求解器将尝试在 "OUTOFCORE "内存模式下运行。
  - `INCORE` - In-core memory mode (核心内存模式)\
  Use a memory allocation strategy in the sparse solver that will attempt to obtain enough memory to run with the entire factorized matrix in memory. This option uses the most amount of memory and should avoid doing any I/O. By avoiding I/O, this option achieves optimal solver performance. However, a significant amount of memory is required to run in this mode, and it is only recommended on machines with a large amount of memory. If the allocation for in-core memory fails, the solver will automatically revert to out-of-core memory mode.\
  在稀疏求解器中使用内存分配策略，尝试获取足够的内存，以便在内存中运行整个因式分解矩阵。该选项使用的内存最多，并应避免执行任何 I/O。通过避免 I/O，该选项可以获得最佳的求解性能。不过，在此模式下运行需要大量内存，因此只建议在内存较大的机器上使用。如果内核内存分配失败，求解器将自动恢复到外核内存模式。
  - `OUTOFCORE` - Out-of-core memory mode. (外核内存模式)\
  Use a memory allocation strategy in the sparse solver that will attempt to allocate only enough work space to factor each individual frontal matrix in memory, but will store the entire factorized matrix on disk. Typically, this memory mode results in poor performance due to the potential bottleneck caused by the I/O to the various files written by the solver.\
  在稀疏求解器中使用内存分配策略，尝试只分配足够的工作空间在内存中对每个单独的正面矩阵进行因式分解，但将整个因式分解后的矩阵存储在磁盘上。通常情况下，这种内存模式会导致性能低下，因为求解器写入的各种文件的 I/O 可能会造成瓶颈。

  mxpand : *`int`* , *`optional`*
  : Number of modes or array name (enclosed in percent signs) to expand and write. If -1, do not expand and do not write modes to the results file during the analysis. Default `""`.\
  要展开和写入的模态阶数或数组名（用百分号括起来）。如果为-1，则在分析过程中不展开也不向结果文件写入模态。默认值为 `""`。

  elcalc : *`bool`* , *`optional`*
  : Calculate element results, reaction forces, energies, and the nodal degree of freedom solution. Default `False`.\
  计算元素结果、反作用力、能量和节点自由度解。默认为 `False`。

Returns:
----------

  `str`
  : Output from MAPDL SOLVE command.

Notes
-------

For models that involve a non-symmetric element stiffness matrix, as in the case of a contact element with frictional contact, the QRDAMP eigensolver (MODOPT, QRDAMP) extracts modes in the modal subspace formed by the eigenmodes from the symmetrized eigenproblem. The QRDAMP eigensolver symmetrizes the element stiffness matrix on the first pass of the eigensolution, and in the second pass, eigenmodes are extracted in the modal subspace of the first eigensolution pass. For such non- symmetric eigenproblems, you should verify the eigenvalue and eigenmode results using the non-symmetric matrix eigensolver (MODOPT,UNSYM).\
对于涉及非对称元素刚度矩阵的模型，如具有摩擦接触的接触元素，QRDAMP 特征求解器（MODOPT，QRDAMP）从对称特征问题的特征模形成的模态子空间中提取模态。QRDAMP 特征求解器在第一轮特征求解中对称元素刚度矩阵，在第二轮特征求解中，在第一轮特征求解的模态子空间中提取特征模态。对于此类非对称特征问题，应使用非对称矩阵特征分解器（MODOPT,UNSYM）验证特征值和特征模态结果。

The DAMP and QRDAMP options cannot be followed by a subsequent spectrum analysis. The UNSYM method supports spectrum analysis when eigensolutions are real.\
DAMP 和 QRDAMP 选项之后不能再进行频谱分析。当等效解为实数时，UNSYM 方法支持频谱分析。

Examples
-------

Modal analysis using default parameters for the first 6 modes\
使用默认参数对前 6 个模态进行模态分析

```python
>>> mapdl.modal_analysis(nmode=6)
```

````