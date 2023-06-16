# Processor entry

{numref}`processor_entry` 这些 SESSION 命令用于进入和退出程序中的各个处理器。

```{table} Processor entry commands
:name: processor_entry

| | |
|---|---|
| `**Mapdl.aux2(**kwargs)**` | 进入二进制文件转储处理器。 |
| `**Mapdl.aux3(**kwargs)**` | 进入结果文件编辑处理器。 |
| `**Mapdl.aux12(**kwargs)**` | "Enters the radiation processor." |
| `**Mapdl.aux15(**kwargs)**` | 进入 IGES 文件传输处理器。 |
| `**Mapdl.finish(**kwargs)**` | 从处理器正常退出。 |
| `**Mapdl.map([kdim,kout,limit])**` | 将压力从源点映射到目标表面单元。 |
| `**Mapdl.post1(**kwargs)**` | 进入数据库结果后处理程序。 |
| `**Mapdl.post26(**kwargs)**` | 进入时间历程后处理程序 |
| `**Mapdl.prep7(**kwargs)**` | 进入前处理器 |
| `**Mapdl.quit(**kwargs)**` | 退出处理器 |
| `**Mapdl.slashsolu(**kwargs)**` | 进入求解器 |

```

```{margin} **IGES**
一种三维建模通用 CAD 格式
```