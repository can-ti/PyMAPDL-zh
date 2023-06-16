# nopr

```{py:method} Mapdl.nopr(**kwargs)

Suppresses the expanded interpreted input data listing.

APDL Command: /NOPR

Notes
------

Suppresses printout of interpreted input data, including information labeled as “Notes.” When this printout is not suppressed, the data input to the analysis is echoed to the output file in an expanded format. Printout is suppressed until a `/GOPR` or `/GO` command is read.\
抑制解释的输入数据的打印输出，包括标为 "注释 "的信息。当这个打印输出没有被抑制时，输入到分析中的数据会以扩展的格式回传到输出文件中。在读取`/GOPR`或`/GO`命令之前，打印输出是被抑制的。

Use of `/NOPR` is not recommended when the graphical user interface (GUI) is active. The GUI sometimes issues “hidden” `/NOPR` and `/GOPR` command sequences, which will countermand user-issued `/NOPR` commands, thus making the use of `/NOPR` in the GUI environment 
unpredictable.\
当图形用户界面（GUI）处于活动状态时，不建议使用`/NOPR`。GUI有时会发出 "隐藏的"`/NOPR`和`/GOPR`命令序列，这将反驳用户发出的`/NOPR`命令，从而使`/NOPR`在GUI环境中的使用变得不可预测。

This command is valid in any processor.

```