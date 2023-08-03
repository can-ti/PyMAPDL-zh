# open_apdl_log

````{method} Mapdl.open_apdl_log(filename, mode='w')

Start writing all APDL commands to an MAPDL input file.\
开始将所有 APDL 命令写入 MAPDL 输入文件。

Parameters:
----------

  filename : *`str`*
  : Filename of the log.

  mode : *`str`* , *`optional`*
  : Python file modes (for example, `'a'`, `'w'`). Should be either write or append.

Examples
----------

Begin writing APDL commands to `"log.inp"`.

```python
>>> mapdl.open_apdl_log("log.inp")
```


````