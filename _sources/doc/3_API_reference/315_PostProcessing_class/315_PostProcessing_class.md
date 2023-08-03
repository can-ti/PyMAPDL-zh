# PostProcessing class

The `PostProcessing` class supports postprocessing directly from the MAPDL live instance. If you want to postprocess MAPDL result files outside of PyMAPDL, you can use one of these packages:\
`PostProcessing` 类支持直接从 MAPDL 实时实例进行后处理。如果您想在 PyMAPDL 之外对 MAPDL 结果文件进行后处理，可以使用这些软件包之一：

- [PyDPF-Core](https://dpf.docs.pyansys.com/dev/) : Postprocessing using the Data Processing Framework (DPF). DPF-Core provides more complex and more powerful postprocessing APIs.\
使用数据处理框架（DPF）进行后处理。DPF-Core 提供更复杂、更强大的后处理 API。

- [PyDPF-Post](https://post.docs.pyansys.com/dev/) : Streamlined and simplified DPF postprocessing. PyDPF-Post is a higher-level package that uses PyDPF-Core.\
精简和简化的 DPF 后处理。PyDPF-Post 是一个使用 PyDPF-Core 的高级软件包。

- [PyMAPDL Reader](https://reader.docs.pyansys.com/): Legacy result file reader. PyMAPDL Reader supports result files for MAPDL 14.5 and later.\
传统结果文件阅读器。PyMAPDL 阅读器支持 MAPDL 14.5 及更高版本的结果文件。

```{table}
| | | |
|---|---|---|
| {doc}`post.PostProcessing(mapdl) <../PostProcessing/PostProcessing>` | Post-processing using an active MAPDL session | 使用活动的 MAPDL 会话进行后处理 |

```

