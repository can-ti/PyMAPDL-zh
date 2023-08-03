# read

````{method} ansXpl.read(recordname, asarray=False)

Read a record and return either an APDL math matrix or an APDL math vector.\
读取记录并返回 APDL math 矩阵或 APDL math 向量。

Returns:
-------
  `ansys.mapdl.AnsMat` or `ansys.mapdl.AnsVec`
  : A handle to the APDLMath object.\
  APDLMath 对象的句柄。

  asarray : *`bool`* , *`optional`*
  : Return a `numpy.ndarray` rather than a `AnsMat`. Default `False`.


Examples
---------

```python
>>> vec = xpl.read('MASS')
>>> vec.asarray()
array([ 4,  7, 10, 13, 16, 19, 22, 25, 28, 31, 34, 37, 40, 43,
       46, 49, 52, 55, 58,  1], dtype=int32)
>>> vec = xpl.read('MASS', asarray=True)
array([ 4,  7, 10, 13, 16, 19, 22, 25, 28, 31, 34, 37, 40, 43,
       46, 49, 52, 55, 58,  1], dtype=int32)
```


````