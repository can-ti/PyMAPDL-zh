# next_available

````{method} LocalMapdlPool.next_available(return_index=False)

Wait until an instance of mapdl is available and return that instance.\
等待 mapdl 实例可用，并返回该实例。

Parameters:
----------

  return_index : *`bool`* , *`optional`*
  : Return the index along with the instance. Default `False`.\
  返回索引和实例。默认为 `False`。

Returns:
----------

  `pyansys.MapdlGrpc`
  :Instance of MAPDL.

  `int`
  : Index within the pool of the instance of MAPDL. By default this is not returned.\
  MAPDL 实例池中的索引。默认情况下不返回。

Examples
---------

```python
>>> mapdl = pool.next_available()
>>> print(mapdl)
Product:         ANSYS Mechanical Enterprise
MAPDL Version:   RELEASE                    BUILD  0.0      UPDATE        0
PyANSYS Version: 0.55.1
```







````