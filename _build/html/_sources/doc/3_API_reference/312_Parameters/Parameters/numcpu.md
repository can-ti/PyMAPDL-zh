# numcpu
 
````{property} property Parameters.numcpu: int]

Number of Distributed MAPDL processes being used.\
正在使用的分布式 MAPDL 进程数量。

Notes
------

This will always return 1 when using shared memory parallel.\
在使用共享内存并行时，该值将始终返回 1。

Examples
--------

```python
>>> mapdl.parameters.numcpu
2
```


````