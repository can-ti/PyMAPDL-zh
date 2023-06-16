# Run controls

{numref}`run_controls` 这些 SESSION 命令控制会话的整体特征，包括作业名称、图形用户界面行为和文件切换。

```{table} Run controls commands
:name: run_controls

| | |
|---|---|
| `**Mapdl.config([lab,value])**` | 为 ANSYS 配置参数赋值。 |
| `**Mapdl.cwd([dirpath])**` | 改变当前的工作目录。 |
| `**Mapdl.exit([save,force])**` | 退出 MAPDL |
| `**Mapdl.filname([fname,key])**` | 为分析更改作业名称。 |
| `**Mapdl.input([fname,ext,dir_,line,log,...])**` | 将本地输入文件传输到远程 mapdl 实例。 |
| `**Mapdl.keyw([keyword,ley])**` | 设置 GUI 用于上下文筛选的关键字(GUI)。 |
| `**Mapdl.memm([lab,kywrd])**` | 允许当前会话保持分配的内存。 |
| `**Mapdl.nerr([nmerr,nmabt,abort,ifkey,num])**` | 限制所显示的警告和错误消息的数量。 |
| `**Mapdl.pause(**kwargs)**` | 暂时释放当前的产品许可证。 |
| `**Mapdl.slashstatus([lab])**` | 列出运行项的状态。 |
| `**Mapdl.starstatus([par,imin,imax,jmin,...])**` | 列出当前参数和缩写。 |
| `**Mapdl.syp([string,arg1,arg2,arg3,arg4,...])**` | 向操作系统传递命令字符串和参数。 |
| `**Mapdl.sys(cmd)**` | 向操作系统传递命令字符串。 |
| `**Mapdl.unpause(**kwargs)**` | 恢复临时释放的产品许可证的使用。 |

```

