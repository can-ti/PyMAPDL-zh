# save

```{py:method} Mapdl.save(fname='', ext='', slab='', **kwargs)

Saves all current database information.\
保存所有当前的数据库信息。

APDL Command: `SAVE`

Parameters:
-----------

  *fname*
  : File name and directory path (248 characters maximum, including the characters needed for the directory path). An unspecified directory path defaults to the working directory; in this case, you can use all 248 characters for the file name.

  *ext*
  : Filename extension (eight-character maximum).

  *slab*
  : Mode for saving the database: 保存数据库的模式：\
  ***All*** --- Save the model data, solution data and post data (element tables, etc.). This value is the default.\
  ***MODEL*** --- Save the model data (solid model, finite element model, loadings, etc.) only.\
  ***SOLU*** --- Save the model data and the solution data (nodal and element results).

Notes
-----

Saves all current database information to a file (File.DB). In interactive mode, an existing File.DB is first written to a backup file (File.DBB). In batch mode, an existing File.DB is replaced by the current database information with no backup. The command should be issued periodically to ensure a current file backup in case of a system “crash” or a “line drop.” It may also be issued before a “doubtful” command so that if the result is not what was intended the database may be easily restored to the previous state. A save may be time consuming for large models. Repeated use of this command overwrites the previous data on the file (but a backup file is first written during an interactive run). When issued from within POST1, the nodal boundary conditions in the database (which were read from the results file) will overwrite the nodal boundary conditions existing on the database file.\
将所有当前的数据库信息保存到一个文件（File.DB）。在交互模式下，现有的File.DB首先被写入一个备份文件 （File.DBB）。在批处理模式下，现有的 File.DB 被当前的数据库信息所取代，没有备份。该命令应该定期发布，以确保在系统 "崩溃 "或 "掉线 "的情况下有一个当前的文件备份。它也可以在一个 "不确定"的命令之前发出，这样如果结果与预期不符，数据库就可以很容易地恢复到以前的状态。对于大型模型来说，保存可能很耗时。重复使用这个命令会覆盖文件上以前的数据（但在交互式运行中会首先写入一个备份文件）。当从 POST1 中发出时，数据库中的节点边界条件（从结果文件中读取）将覆盖数据库文件上已有的节点边界条件。

Internal nodes may be created during solution (for example, via the mixed u-P formulation or generalized plane strain option for current-technology elements, the Lagrangian multiplier method for contact elements or the MPC184 elements, or the quadratic or cubic option of the BEAM188 and PIPE288 elements). It is sometimes necessary to save the internal nodes in the database for later operations, such as cutting boundary interpolations (CBDOF) for submodeling. To do so, issue the SAVE command after the first SOLVE command.\
内部节点可以在求解过程中创建（例如，通过混合 u-P 公式或当前技术单元的广义平面应变选项，接触单元或MPC184元素的拉格朗日乘法，或 BEAM188 和 PIPE288 单元的二次方或三次方选项）。有时有必要将内部节点保存在数据库中，以便以后的操作，例如用于子模型的切割边界插值（CBDOF）。要做到这一点，在第一个 `SOLVE` 命令后发出 `SAVE` 命令。

In general, saving after solving is always a good practice.\
一般来说，求解之后就随时保存总是一种好的做法。

This command is valid in any processor.

```