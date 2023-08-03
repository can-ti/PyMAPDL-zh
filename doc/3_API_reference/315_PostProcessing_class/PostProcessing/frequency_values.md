# frequency_values\

````{property} property PostProcessing.frequency_values: ndarray

Return an array of the frequency values for all result sets.\
返回所有结果集的频率值数组。

Returns:
--------

  `numpy.ndarray`
  : Numpy array of the frequency values for all result sets.\
  包含所有结果集频率值的 Numpy 数组。

Examples
--------

Get all the time values after loading POST1.

```python
>>> mapdl.post1()
>>> mapdl.post_processing.frequency_values
array([ 220.,  240.,  260.,  280.,  300.,  320.,  340.,  360.,  380.,
400.,  420.,  440.])
```



````