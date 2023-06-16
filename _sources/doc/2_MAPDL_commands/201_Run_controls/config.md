# config


```{py:method} Mapdl.config(lab='', value='', **kwargs)

为 ANSYS “配置参数”赋值。

APDL Command: /CONFIG

Parameters:
-------------------

  *lab*
  : 要改变的配置参数：

    *NORSTGM* - 选择写入或不写入几何数据到结果文件。
    : VALUE 为 0（写入几何数据）或 1（不写入几何数据）。当复杂的分析会产生异常大的文件时，该值非常有用。默认值为0。

    *NBUF* - VALUE 是指求解器中每个文件的缓冲区数量（1 到 32）。
    : 默认值为 4.

    *LOCFL* - 文件的打开和关闭动作。
    : 对于 VALUE 使用：0 代表全局（默认）；1 代表本地。适用于 File.EROT、File.ESAV 和 File.EMAT。通常用于大型问题，在这些问题中，可以用 /FDELE 命令在运行初期删除本地关闭的文件。

    *SZBIO* - VALUE 是二进制文件的记录大小（1024 至 4194304）（以整数字为单位）。
    : 默认为 16384（取决于计算机系统）。

    *ORDER* - 自动重新排序方案。
    : 对于 VALUE 的使用：0 代表 WSORT,ALL；1 代表 WAVES；2 代表 WSORT,ALL 和 WAVES（默认）。

    *FSPLIT* - 定义二进制文件的分割点。
    : VALUE 是文件分割点，单位是兆字，默认为系统的最大文件大小。

    *MXND* - Maximum number of nodes.
    : 如果没有指定，第一次遇到时默认为 100。当超过最大限度时，即使在第一次遇到时也会动态地扩大一倍。
      
    *MXEL* - Maximum number of elements.
    : Default and expansion as for MXND.

    *MXKP* - Maximum number of keypoints.
    : Default and expansion as for MXND.

    *MXLS* - Maximum number of lines.
    : Default and expansion as for MXND.

    *MXAR* - Maximum number of areas.
    : Default and expansion as for MXND.

    *MXVL* - Maximum number of volumes.
    : Default and expansion as for MXND.

    *MXRL* - Maximum number of sets of real constants (element attributes).
    : Default and expansion as for MXND.

    *MXCP* - Maximum number of sets of coupled degrees of freedom.
    : Default and expansion as for MXND.

    *MXCE* - Maximum number of constraint equations.
    : Default and expansion as for MXND.

    *NOELDB* - 可以选择在求解完成后是否将结果数据写入数据库。
    : 当 VALUE = 0（默认）时，将结果写入数据库。当 VALUE = 1 时，不将结果写入数据库。

    *DYNA_DBL* - 调用显式动力学求解器 LS-DYNA 的双精度版本的选项。
    : 当 VALUE = 0（默认）时，使用单精度版本。当 VALUE = 1 时，使用双精度版本。

    ***STAT* - 显示 /CONFIG 命令设置的当前值。**

  *value*
  : 分配给配置参数的值（一个整数）。

Notes
----------
所有的配置参数都有初始默认值，在大多数情况下不需要改变。当需要一个特殊配置的 ANSYS 程序版本时，可以用这个命令改变参数。 **`Mapdl.config(STAT)`** 来显示当前值。更改必须在参数需要之前定义。这些改变（和其他的）也可以纳入到 `config162.ans` 文件中，该文件在程序执行时被读取（见 The Configuration File in the *Basic Analysis Guide*）。如果相同的配置参数同时出现在配置文件和本命令中，本命令将优先处理。

分布式 ANSYS 使用默认的 *FSPLIT* 值，并强制所有结果文件的 *NOELDB = 1* 和 *NORSTGM = 0*。当使用分布式 ANSYS 时，*FSPLIT*、*NOELDB* 和 *NORSTGM* 选项不能被改变。

/CONFIG 命令对 ANSYS Multiphysics 1、2 或 3 产品无效。

ANSYS 多场求解器（MFS 和 MFX）不支持 */CONFIG,NOELDB,1*。ANSYS 多场求解器需要更新 ANSYS 数据库。

```

------------------------

```{py:method} Mapdl.config(lab='', value='', **kwargs)

Assigns values to ANSYS configuration parameters.

APDL Command: /CONFIG

Parameters:
--------------

  *lab*
  : Configuration parameter to be changed:

    *NORSTGM* - Option to write or not write geometry data to the results file.
    : VALUE is either 0 (write geometry data) or 1 (do not write geometry data). Useful when complex analyses will create abnormally large files. Default is 0.

    *NBUF* - VALUE is the number of buffers (1 to 32) per file in the solver.
    : Defaults to 4.

    *LOCFL* - File open and close actions.
    : For VALUE use: 0 for global (default); 1 for local. Applicable to File.EROT, File.ESAV, and File.EMAT. Typically used for large problems where locally closed files may be deleted earlier in the run with the /FDELE command.

    *SZBIO* - VALUE is the record size (1024 to 4194304) of binary files (in integer words).
    : Defaults to 16384 (system dependent).

    *ORDER* - Automatic reordering scheme.
    : For VALUE use: 0 for WSORT,ALL; 1 for WAVES; 2 for both WSORT,ALL and WAVES (default).

    *FSPLIT* - Defines split points for binary files.
    : VALUE is
the file split point in megawords and defaults to the maximum file size for the system.

    *MXND* - Maximum number of nodes.
    : If not specified, defaults to 100 at first encounter. Dynamically expanded by doubling, even at first encounter, when maximum is exceeded.
      
    *MXEL* - Maximum number of elements.
    : Default and expansion as for MXND.

    *MXKP* - Maximum number of keypoints.
    : Default and expansion as for MXND.

    *MXLS* - Maximum number of lines.
    : Default and expansion as for MXND.

    *MXAR* - Maximum number of areas.
    : Default and expansion as for MXND.

    *MXVL* - Maximum number of volumes.
    : Default and expansion as for MXND.

    *MXRL* - Maximum number of sets of real constants (element attributes).
    : Default and expansion as for MXND.

    *MXCP* - Maximum number of sets of coupled degrees of freedom.
    : Default and expansion as for MXND.

    *MXCE* - Maximum number of constraint equations. Default and expansion as for MXND.

    *NOELDB* - Option to write or not write results into the database after a solution.
    : When VALUE = 0 (default), write results into the database. When VALUE = 1, do not write results into the database.

    *DYNA_DBL* - Option to invoke the double precision version of the explicit dynamics solver LS-DYNA.
    : When VALUE = 0 (default), the single precision version is used. When VALUE = 1, the double precision version is used.

    ***STAT* - Displays current values set by the /CONFIG command.**

  *value*
  : Value (an integer number) assigned to the configuration parameter.


Notes
----------

All configuration parameters have initial defaults, which in most cases do not need to be changed. Where a specially configured version of the ANSYS program is desired, the parameters may be changed with this command. Issue /CONFIG,STAT to display current values. Changes must be defined before the parameter is required. These changes (and others) may also be incorporated into the config162.ans file which is read upon execution of the program (see The Configuration File in the Basic Analysis Guide). If the same configuration parameter appears in both the configuration file and this command, this command overrides.

Distributed ANSYS uses the default FSPLIT value, and forces NOELDB = 1 and NORSTGM = 0 for all results files. The FSPLIT, NOELDB, and NORSTGM options cannot be changed when using Distributed ANSYS.

The /CONFIG command is not valid for the ANSYS Multiphysics 1, 2, or 3 products.

The ANSYS Multi-field solver (MFS and MFX) does not support /CONFIG,NOELDB,1. The ANSYS Multi-field solver needs the updated ANSYS database.

```

