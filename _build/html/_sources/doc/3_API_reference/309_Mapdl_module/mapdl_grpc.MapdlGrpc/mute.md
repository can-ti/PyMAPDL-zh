# mute

````{property} property MapdlGrpc.mute

Silence the response from all MAPDL functions unless explicitly set to `True`.\
静音所有 MAPDL 函数的响应，除非明确设置为 `True`。

Returns:
--------

  `bool`
  : Current state of the mute.

Examples
------

```python
>>> mapdl.mute = True
>>> mapdl.prep7()
''
```

Temporarily override the instance setting this with `mute=False`. This is useful for methods that parse the MAPDL output like `k`.\
用 `mute=False`临时覆盖实例设置。这对解析 MAPDL 输出（如 `k`）的方法非常有用。

```python
>>> mapdl.k('', 1, 1, 1, mute=False)
1
```


````