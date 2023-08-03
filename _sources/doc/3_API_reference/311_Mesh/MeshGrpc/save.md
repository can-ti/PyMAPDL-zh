# save

````{method} MeshGrpc.save(filename, binary=True, force_linear=False, allowable_types=None, null_unallowed=False)

Save the geometry as a vtk file.\
将几何图形保存为 vtk 文件。

Parameters:
---------

  filename : *`str`* , *`[pathlib.Path](https://docs.python.org/3/library/pathlib.html#pathlib.Path)`*
  : Filename of output file. Writer type is inferred from the extension of the filename.\
  输出文件的文件名。根据文件名的扩展名推断出写入器类型。

  binary : *`bool`* , *`optional`*
  : If `True`, write as binary, else ASCII.\
  如果 `True`，则写成二进制，否则写成 ASCII.

  force_linear : *`bool`* , *`optional`*
  : This parser creates quadratic elements if available. Set this to `True` to always create linear elements. Defaults to `False`.\
  如果可用，该解析器会创建二次单元。设为 `True` 则始终创建线性单元。默认为 `False`。

  allowable_types : *`list`* , *`optional`*
  : Allowable element types. Defaults to all valid element types in `ansys.mapdl.reader.elements.valid_types`.
See `help(ansys.mapdl.reader.elements)` for available element types.\
  允许的单元类型。默认为 `ansys.mapdl.reader.elements.valid_types` 中的所有有效单元类型。 有关可用单元类型，请参阅 `help(ansys.mapdl.reader.elements)`。

  null_unallowed : *`bool`* , *`optional`*
  : Elements types not matching element types will be stored as empty (null) elements. Useful for debug or tracking element numbers. Default `False`.\
  与单元类型不匹配的单元将被存储为空（null）单元。有助于调试或跟踪单元数量。默认为 `False`.

Notes
---------

Binary files write much faster than ASCII and have a smaller file size.\
二进制文件的写入速度比 ASCII 快得多，文件大小也较小。



````