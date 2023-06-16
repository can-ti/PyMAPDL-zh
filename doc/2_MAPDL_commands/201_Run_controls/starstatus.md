# starstatus

```{py:method} Mapdl.starstatus(par='', imin='', imax='', jmin='', jmax='', kmin='', kmax='', lmin='', lmax='', mmin='', mmax='', kpri='', **kwargs)

Lists the current parameters and abbreviations.\
列出当前的参数和缩略词。

APDL Command: `*STATUS`

Parameters:
------------

  *par*
  : Specifies the parameter or sets of parameters listed. For array parameters, use IMIN, IMAX, etc. to specify ranges. Use `*DIM` to define array parameters. Use `*VEDIT` to review array parameters interactively. Use `*VWRITE` to print array values in a formatted output. If Par is blank, list all scalar parameter values, array parameter dimensions, and abbreviations. If ARGX, list the active set of local macro parameters (ARG1 to ARG9 and AR10 to AR99) [`*USE`].\
  指定列出的参数或参数集。对于数组参数(array)，使用 *IMIN、IMAX* 等来指定范围。使用 `*DIM` 来定义数组参数。使用 `*VEDIT` 可以交互式的查看数组参数。使用 `*VWRITE` 可以格式化的输出中打印数组值。如果 `*Par*` 是空白，则会列出所有标量参数值，数组参数维度都和缩写。如果是 `*ARGX*`，则会列出活动的本地宏参数集（ARG1 - ARG9 和 AR10- AR99）[`*USE`]。
  The following are possible values for Par:

    *ALL or blank --*
    : Lists all parameters (except local macro parameters and those with names beginning or ending with an underbar) and toolbar abbreviations.\
    列出所有的参数（除了本地宏参数和名称以下划线开头或结尾的参数）和工具条缩写。

    *_PRM --*
    : Lists only parameters with names beginning with an underbar(_). These are ANSYS internal parameters.\
    只列出名称以下划线(_)开头的参数。这些是ANSYS的内部参数。

    *PRM_--*
    : Lists only parameters with names ending with an underbar (_). A good APDL programming convention is to ensure that all parameters created by your system programmer are named with a trailing underbar. \
    只列出名称以下划线（_）结尾的参数。一个好的 APDL 编程习惯是确保所有由你的系统程序员创建的参数都以尾部的下划线来命名。

    *ABBR --*
    : Lists all toolbar abbreviations.\
    列出所有工具条的缩写。

    *PARM --*
    : Lists all parameters (except local macro parameters and those with names beginning or ending with an underbar). \
    列出所有的参数（除了本地宏参数和名称以下划线开头或结尾的参数）。

    *MATH --*
    : Lists all APDL Math parameters, including vectors, matrices, and linear solvers.\
    列出所有 APDL math 参数，包括向量、矩阵和线性求解器。

    *PARNAME--*
    : Lists only the parameter specified. PARNAME cannot be a local macro parameter name.\
    只列出指定的参数。*PARNAME* 不能是本地宏参数名称。

    *ARGX*
    : Lists all local macro parameter values (ARG1- AR99) that are non-zero or non-blank.\
    列出所有非零或非空白的本地宏参数值（ARG1-AR99）。

  *imin, imax, jmin, jmax, kmin, kmax, lmin, lmax, mmin, mmax*
  : Range of array elements to display (in terms of the dimensions (row, column, plane, book, and shelf)). Minimum values default to 1. Maximum values default to the maximum dimension values. Zero may be input for IMIN, JMIN, and KMIN to display the index numbers. See `*TAXIS` command to list index numbers of 4- and 5-D tables.\
  要显示的数组元素的范围（根据维度（row、column、plane、book和shelf））。最小值默认为 1。最大值默认为最大维度值。IMIN、JMIN 和 KMIN 可以输入 zero 来显示索引号。参见`*TAXIS`命令，列出 4-D 和 5-D 表格的索引号。

  *kpri*
  : Use this field to list your primary variable labels (X, Y, Z, TIME, etc.).\
  使用这个字段来列出你的主要变量标签（X、Y、Z、TIME等）。\
  1 --- List the labels (default). YES, Y, or ON are also valid entries.\
  2 --- Do not list the labels. NO, N, or OFF are also valid entries.

Notes
----------

You cannot obtain the value for a single local parameter (e.g., `*STATUS,ARG2`). You can only request all local parameters simultaneously using `*STATUS,ARGX`.\
你不能获得单个本地参数的值（例如，`*STATUS,ARG2`）。你只能使用 `*STATUS,ARGX` 同时请求所有的本地参数。

This command is valid in any processor.

```