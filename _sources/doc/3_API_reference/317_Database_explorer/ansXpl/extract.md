# extract

````{method} ansXpl.extract(recordname, sets='ALL', asarray=False)

Import a Matrix/Vector from a MAPDL result file.\
从 MAPDL 结果文件导入矩阵/矢量。

At the moment, this only supports reading the displacement vectors from a result file.\
目前，它只支持从结果文件中读取位移矢量。

Parameters:
---------

  recordname: *`str`*
  : Record name. Currently only supports the `"NSL"` record, displacement vectors.\
  记录名称。目前只支持 `"NSL"` 记录和位移矢量。

  sets: *`str`* or *`int`*
  : Number of sets. Can be `"ALL"` or the number of sets to load.\
  数据集数量。可以是 `"ALL"`，也可以是要加载的数据集数。

  asarray: *`bool`* , *`optional`*
  : Return a `numpy.ndarray` rather than a `AnsMat`. Default `False`.\
  返回 `numpy.ndarray` 而不是 `AnsMat`。默认为 `假`。

Returns:
-------

  `numpy.ndarray` or `{doc}`ansys.mapdl.core.math.AnsMat <../AnsMat/AnsMat>``
  : A `numpy.ndarray` or `{doc}`AnsMat <../AnsMat/AnsMat>`` of the displacement vectors, depending on the value of `asarray`.\


Notes
------

This only works on the `"NSL"` record of MAPDL result files.\
这仅适用于 MAPDL 结果文件中的 `"NSL"` 记录。


Examples
---------

First, open a result file and extract the displacement vectors for all sets.\
首先，打开结果文件，提取所有集合的位移矢量。

```python
>> xpl.open("file.rst")
>> mat = xpl.extract("NSL")
>> mat
Dense APDLMath Matrix (243, 10)
```

Convert to a dense numpy array\
转换为密集的 numpy 数组

```python
>>> arr = mat.asarray()
>>> arr
array([[-9.30806802e-03, -2.39600770e-02, -5.37856729e-03, ...,
        -5.61188243e-03, -7.17686067e-11,  3.71893252e-03],
       [-1.60960014e-02,  2.00410618e-02,  8.05822565e-03, ...,
        -1.26917511e-02, -5.14133724e-11, -1.38783485e-03],
       [ 2.54040694e-02,  3.91901513e-03, -2.67965796e-03, ...,
        -1.46365178e-02,  8.31735188e-11, -2.33109771e-03],
       ...,
       [-2.80679551e-03, -1.45686692e-02,  8.05466291e-03, ...,
         5.88196684e-03,  1.72211103e-02,  6.10079082e-03],
       [-7.06675717e-03,  1.30455037e-02, -6.31685295e-03, ...,
         1.08619340e-02, -1.72211102e-02,  2.52199472e-03],
       [ 2.29726170e-02,  3.54392176e-03, -1.87020162e-03, ...,
         1.20642736e-02,  2.58299321e-11,  9.14504940e-04]])
```



````