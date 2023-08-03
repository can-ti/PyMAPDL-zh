# time_values

````{property} property PostProcessing.time_values: ndarray

Return an array of the time values for all result sets.

Returns:
-------

  `numpy.ndarray`
  : Numpy array of the time values for all result sets.

Examples
---------

Get all the time values after loading POST1.\
加载 POST1 后获取所有时间值。

```python
>>> mapdl.post1()
>>> mapdl.post_processing.time_values
[75.00054133588232,
 75.00081189985094,
 75.00121680412036,
 75.00574491751847,
 75.03939292229019,
 75.20949687626468]
```



````