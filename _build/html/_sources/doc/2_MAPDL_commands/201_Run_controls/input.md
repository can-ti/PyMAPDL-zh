# input

````{py:method} Mapdl.input(fname='', ext='', dir_='', line='', log='', *, verbose=False, progress_bar=False, time_step_stream=None, chunk_size=512, orig_cmd='/INP', write_to_log=True, **kwargs)

Stream a local input file to a remote mapdl instance. Stream the response back and deserialize the output.\
将本地输入文件实时流式传输到远程Mapdl实例。将响应流传回并反序列化输出。

```{admonition} Changed in version 0.65: 
From version 0.65 you can use the APDL commands arguments (`ext`, `dir`, `line`) in within this command. However, the gRPC implementation does not uses the APDL `/INPUT` command, rather the gRPC input method with the appropriate configuration to replicate `/INPUT` behaviour.\
从 0.65 版本开始，你可以在这个命令中使用 APDL 命令的参数（`ext`, `dir`, `line`）。然而，gRPC 的实现并不使用 APDL 的 `/INPUT` 命令，而是使用具有适当配置的 gRPC 输入方法来仿制 `/INPUT` 行为。
```

Parameters:
-------------

  *fname*: `str`
  : MAPDL input file to stream to the MAPDL grpc server. File name and directory path. An unspecified directory path defaults to the Python working directory; in this case, you can use all 248 characters for the file name. The file name defaults to the current `Jobname` if `Ext` is specified.\
  要流向 MAPDL grpc 服务器的 MAPDL 输入文件。文件名和目录路径。未指定的目录路径默认为 Python 工作目录；在这种情况下，你可以使用所有 248 个字符作为文件名。如果指定 `Ext`，文件名默认为当前的 `Jobname`。
  
  *ext:* `str`
  : Filename extension (eight-character maximum).\
  文件名扩展名（最多8个字符）。

  *dir:* `str`
  : Directory path. Defaults to current directory.\
  目录路径。默认为当前目录。

  *line:* `int`
  : A value indicating either a line number in the file from which to begin reading the input file. The first line is the zero line (Python convention).\
  一个表示文件中的行号的值，从该行开始读取输入文件。第一行是 0 行( Python 惯例)。
    - **(blank), or 0** --- Begins reading from the top of the file (default).
    - **LINE_NUMBER** --- Begins reading from the specified line number in the file.

  *log*
  : Not supported in the gRPC implementation.\
  不支持在 gRPC 中执行。

  *time_step_stream:* `int`
  : Time to wait between streaming updates to send back chunks from the listener file. Larger values mean more data per chunk and less chunks, but if the command is short, will wait until time_step_stream is finished leading to a long execution time.\
  在流式更新之间等待从监听器文件发回块的时间。较大的值意味着每块数据更多，块数更少，但如果命令很短，会等到 time_step_stream 完成，导致执行时间很长。\
  Due to stability issues, the default time_step_stream is dependent on verbosity. The defaults are:\
  由于稳定性问题，默认的 time_step_stream 取决于 verbosity。默认值为：
  - `verbose=True` : `time_step_stream=500`
  - `verbose=False` : `time_step_stream=50`

    These defaults will be ignored if time_step_stream is manually set.\
    如果手动设置了 time_step_stream，这些默认值将被忽略。

  *orig_cmd:* `str`
  : Original command. There are some cases, were input is used to send the file to the grpc server but then we want to run something different than `/INPUT`, for example `CDREAD`.\
  原始命令。在某些情况下，input 用于将文件发送到 grpc 服务器，但是我们希望运行与 `/INPUT` 不同的内容，例如 `CDREAD`。

Returns:
-----------------

  `str`
  : Response from MAPDL.


Notes
----------

This method does not use the APDL /INPUT command. However its usage is very similar to it. See Examples section.\
这种方法不使用 APDL `/INPUT` 命令。但是它的用法与它非常相似。见示例部分。

If you want to use `/INPUT` for some reason, although it is not recommended, you can write the desired input file, upload it using **`Mapdl.upload`**, and then use run command **`Mapdl.run('/INPUT,`**. This does not avoid to use the gRPC input method, but it allows you to use the APDL `/INPUT` command from the generated input file. See *Examples* section for more information.\
如果你出于某种原因想使用 `/INPUT`，虽然不推荐，你可以写出所需的输入文件，用 **`Mapdl.upload`** 上传，然后使用运行命令 **`Mapdl.run('/INPUT,`**。这并不避免使用 gRPC 输入方法，但它允许你从生成的输入文件中使用 APDL `/INPUT` 命令。更多信息请参见 *示例* 部分。

Examples
-------------

Load a simple `"ds.dat"` input file generated from Ansys Workbench.\
加载一个由 Ansys Workbench 生成的简单的 "ds.dat "输入文件。

```python
>>> output = mapdl.input('ds.dat')
```

Load that same file while streaming the output in real-time.\
加载同一文件，同时实时流式输出。

```python
>>> output = mapdl.input('ds.dat', verbose=True)
```

Use the default APDL `/INPUT` command:\

```python
>>> with open('myinput.inp','w').write("/finish\n/prep7\n/com, my commands")
>>> with open('inputtrigger.inp','w').write("/input,myinput,inp")
>>> mapdl.upload("myinput.inp")
Uploading myinput.inp: 100%|█████████████████████████████████████████████████| 26.0/26.0 [00:00<00:00, 5.86kB/s]
'myinput.inp'
>>> mapdl.upload("inputtrigger.inp")
Uploading inputtrigger.inp: 100%|████████████████████████████████████████████| 32.0/32.0 [00:00<00:00, 8.92kB/s]
'inputtrigger.inp'
>>> with mapdl.non_interactive:
        mapdl.run("/input,inputtrigger,inp") # This inputs 'myinput.inp'
```


````