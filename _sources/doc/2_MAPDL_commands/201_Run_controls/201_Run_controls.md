# Run controls

{numref}`run_controls` 这些 SESSION 命令控制会话的整体特征，包括作业名称、图形用户界面行为和文件切换。

```{table} Run controls commands
:name: run_controls

| | | |
|---|---|---|
| {doc}`Mapdl.config([lab,value]) <../201_Run_controls/config>` | Assigns values to ANSYS configuration parameters.|为 ANSYS 配置参数赋值。 |
| {doc}`Mapdl.cwd([dirpath]) <../201_Run_controls/cwd>`|Changes the current working directory.| 改变当前的工作目录。 |
| {doc}`Mapdl.exit([save,force]) <../201_Run_controls/exit>` |Exit MAPDL.| 退出 MAPDL |
| {doc}`Mapdl.filname([fname,key]) <../201_Run_controls/filname>` |Changes the Jobname for the analysis.| 为分析更改作业名称。 |
| {doc}`Mapdl.input([fname,ext,dir_,line,log,...]) <../201_Run_controls/input>` |Stream a local input file to a remote mapdl instance.| 将本地输入文件传输到远程 mapdl 实例。 |
| {doc}`Mapdl.keyw([keyword,ley]) <../201_Run_controls/keyw>` |Sets a keyword used by the GUI for context filtering (GUI).| 设置 GUI 用于上下文筛选的关键字(GUI)。 |
| {doc}`Mapdl.memm([lab,kywrd]) <../201_Run_controls/memm>` |Allows the current session to keep allocated memory.| 允许当前会话保持分配的内存。 |
| {doc}`Mapdl.nerr([nmerr,nmabt,abort,ifkey,num]) <../201_Run_controls/nerr>` |Limits the number of warning and error messages displayed.| 限制所显示的警告和错误消息的数量。 |
| {doc}`Mapdl.pause(**kwargs) <../201_Run_controls/pause>` |Temporarily releases the current product license.| 暂时释放当前的产品许可证。 |
| {doc}`Mapdl.slashstatus([lab]) <../201_Run_controls/slashstatus>` |Lists the status of items for the run.| 列出运行项的状态。 |
| {doc}`Mapdl.starstatus([par,imin,imax,jmin,...]) <../201_Run_controls/starstatus>` |Lists the current parameters and abbreviations.| 列出当前参数和缩写。 |
| {doc}`Mapdl.syp([string,arg1,arg2,arg3,arg4,...]) <../201_Run_controls/syp>` |Passes a command string and arguments to the operating system.| 向操作系统传递命令字符串和参数。 |
| {doc}`Mapdl.sys(cmd) <../201_Run_controls/sys>` |Pass a command string to the operating system.| 向操作系统传递命令字符串。 |
| {doc}`Mapdl.unpause(**kwargs) <../201_Run_controls/unpause>` |Restores use of a temporarily released product license.| 恢复临时释放的产品许可证的使用。 |

```

