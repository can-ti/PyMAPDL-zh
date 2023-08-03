# upload

````{method} MapdlGrpc.upload(file_name, progress_bar=True)

Upload a file to the grpc instance\
向 grpc 实例上传文件

Parameters:
----------

  file_name : *`str`*
  : Local file to upload.

  progress_bar : *`bool`*, *`optional`*
  : Whether to display a progress bar using `tqdm`. The default is `True`. This parameter is helpful for showing download progress.\
  是否使用 `tqdm` 显示进度条。默认为 `True`。该参数有助于显示下载进度。

Returns:
--------

  `str`
  : Base name of the file uploaded. File can be accessed relative to the mapdl instance with this file name.\
  上传文件的基本名称。文件可相对于使用此文件名的 mapdl 实例进行访问。

Examples
----------

Upload “local_file.inp” while disabling the progress bar\
上传 "local_file.inp"，同时禁用进度条

```python
>>> mapdl.upload('local_file.inp', progress_bar=False)
```








````
