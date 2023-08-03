# download

````{method} MapdlGrpc.download(files, target_dir=None, chunk_size=None, progress_bar=None, recursive=False)

Download files from the gRPC instance workind directory\
从 gRPC 实例 workind 目录下载文件

```{warning}
This feature is only available for MAPDL 2021R1 or newer.\
该功能仅适用于 MAPDL 2021R1 或更新版本。
```

Parameters:
--------

  file : *`str`* or *`List`[`str`]* or *`Tuple`(`str`)*
  : Name of the file on the server. File must be in the same directory as the mapdl instance. A list of string names or tuples of string names can also be used. List current files with {doc}`Mapdl.list_files <../mapdl_grpc.MapdlGrpc/list_files>`.\
  服务器上的文件名。文件必须与 mapdl 实例位于同一目录。也可以使用字符串名称列表或字符串名称元组。使用 {doc}`Mapdl.list_files <../mapdl_grpc.MapdlGrpc/list_files>` 列出当前文件。\
  Alternatively, you can also specify **global expressions** to match file names. For example: ‘file*’ to match every file whose name starts with ‘file’.\
  另外，您也可以指定**全局表达式**来匹配文件名。例如：'file*' 用于匹配文件名以 'file' 开头的所有文件。

  target_dir : *`str`* , *`optional`*
  : Path where the downloaded files will be located. The default is the current working directory.\
  下载文件所在的路径。默认为当前工作目录。

  chunk_size : *`int`* , *`optional`*
  : Chunk size in bytes. Must be less than 4MB. The default is 256 kB.\
  分块大小（以字节为单位）。必须小于 4MB。默认值为 256 kB。

  progress_bar : *`bool`* , *`optional`*
  : Display a progress bar using `tqdm` when `True`. Helpful for showing download progress.\
  当为 `True` 时使用 `tqdm` 显示进度条。有助于显示下载进度。

  recursive : *`bool`* , *`optional`*
  : Whether to use recursion when using glob pattern. The default is `False`.\
  使用 glob 模式时是否使用递归。默认为 `False`。

Notes
--------

There are some considerations to keep in mind when using this command:\
使用该命令时需要注意一些事项：

- The glob pattern search does not search recursively in remote instances.\
glob 模式搜索不会在远程实例中进行递归搜索。
- In a remote instance, it is not possible to list or download files in different locations than the MAPDL working directory.\
在远程实例中，无法列出或下载与 MAPDL 工作目录不同位置的文件。
- If you are in local and provide a file path, downloading files from a different folder is allowed. However it is not a recommended approach.\
如果您在本地并提供了文件路径，则允许从不同的文件夹下载文件。但不建议使用这种方法。

Examples
-----------

Download a single file:\
下载单个文件：
```python
>>> mapdl.download('file.out')
```

Download all the files starting with ‘file’:\
下载所有以 "file" 开头的文件：
```python
>>> mapdl.download('file*')
```

Download every single file in the MAPDL workind directory:\
下载 MAPDL workind 目录中的所有文件：
```python
>>> mapdl.download('*.*')
```

Alternatively, you can download all the files using `Mapdl.download_project` (recommended):\
或者，您也可以使用 `Mapdl.download_project` 方法下载所有文件（推荐使用）：
```python
>>> mapdl.download_project()
```



````