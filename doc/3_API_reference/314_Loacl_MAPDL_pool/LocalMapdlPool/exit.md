# exit

````{method} LocalMapdlPool.exit(block=False)

Close out all instances in the pool.

Parameters:
----------

  block : *`bool`* , *`optional`*
  : When `True`, wait until all processes are closed.\
  为 `true` 时，等待所有进程关闭。

Examples
--------

```python
>>> pool.exit()
```


````