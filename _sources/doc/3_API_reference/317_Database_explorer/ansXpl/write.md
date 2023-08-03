# write

````{method} ansXpl.write(recordname, vecname)

Write a given record back to an MAPDL file.\
将给定记录写回 MAPDL 文件。

Use the write function at your own risk, you may corrupt an existing file by changing the size of a record in the file. This method must be used only on a non-compressed file.\
请自行承担使用写入功能的风险，因为改变文件中记录的大小可能会损坏现有文件。此方法只能用于非压缩文件。


Parameters:
----------

  recordname : *`str`*
  : Name of the record you want to overwrite. Your position in the file must be set accordingly to this record location (same as if you want to read it).\
  要覆盖的记录名称。您在文件中的位置必须相应设置为该记录的位置（与您要读取的位置相同）。

  vecname : *`str`*
  : Name of the APDLMath vector you want to write in the MAPDL file. Its size must be consistent with the existing record.\
  要写入 MAPDL 文件的 APDLMath 向量的名称。其大小必须与现有记录一致。

Returns:
-------
  `str`
  : Response from MAPDL.

Examples
--------

```python
>>> xpl.write('MASS', vecname)
```




````