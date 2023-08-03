# freq

````{property} property PostProcessing.freq: float

Frequency associated with current result in the database.\
与数据库中当前结果相关的频率。

Applicable for a Modal, harmonic or spectral analysis.\
适用于模态、谐波或频谱分析。

Examples
--------

Natural frequency of the current result of a modal analysis\
当前模态分析结果的固有频率

```python
>>> mapdl.post1()
>>> mapdl.set(1, 1)
>>> mapdl.post_processing.freq
956.86239847
```


````