# Processor entry

{numref}`processor_entry` 这些 SESSION 命令用于进入和退出程序中的各个处理器。

````{table} Processor entry commands
:name: processor_entry

| | | |
|---|---|---|
| {doc}`Mapdl.aux2(**kwargs) <../202_Processor_entry/aux2>` |Enters the binary file dumping processor.| 进入二进制文件转储处理器。 |
| {doc}`Mapdl.aux3(**kwargs) <../202_Processor_entry/aux3>` |Enters the results file editing processor.| 进入结果文件编辑处理器。 |
| {doc}`Mapdl.aux12(**kwargs) <../202_Processor_entry/aux12>` |Enters the radiation processor.| Enters the radiation processor. |
| {doc}`Mapdl.aux15(**kwargs) <../202_Processor_entry/aux15>` |Enters the IGES file transfer processor.| 进入 IGES 文件传输处理器。 |
| {doc}`Mapdl.finish(**kwargs) <../202_Processor_entry/finish>` |Exits normally from a processor.| 从处理器正常退出。 |
| {doc}`Mapdl.map([kdim,kout,limit]) <../202_Processor_entry/map>` |Maps pressures from source points to target surface elements.| 将压力从源点映射到目标表面单元。 |
| {doc}`Mapdl.post1(**kwargs) <../202_Processor_entry/post1>` |Enters the database results postprocessor.| 进入数据库结果后处理程序。 |
| {doc}`Mapdl.post26(**kwargs) <../202_Processor_entry/post26>` |Enters the time-history results postprocessor.| 进入时间历程后处理程序 |
| {doc}`Mapdl.prep7(**kwargs) <../202_Processor_entry/prep7>` |Enters the model creation preprocessor.| 进入前处理器 |
| {doc}`Mapdl.quit(**kwargs) <../202_Processor_entry/quit>` |Exits a processor.| 退出处理器 |
| {doc}`Mapdl.slashsolu(**kwargs) <../202_Processor_entry/slashsolu>` |Enters the solution processor.| 进入求解器 |

````

