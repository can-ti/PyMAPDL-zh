# ignore_errors

````{property} property Mapdl.ignore_errors: bool

Invalid commands will be ignored rather than exceptions.\
无效的命令将被忽略，而不是出现异常

Normally, any string containing “**ERROR**” from MAPDL will trigger a `MapdlRuntimeError`. Set this to `True` to ignore these errors.\
通常，来自 MAPDL 的任何包含 "**ERROR**"的字符串都会触发 "MapdlRuntimeError"。将其设置为 `True`可忽略这些错误。

For example, a command executed in the wrong processor will raise an exception when `ignore_errors=False`. This is the default behavior.\
例如，当 `ignore_errors=False` 时，在错误处理器中执行的命令会引发异常。这是默认行为。

Examples
----------

```python
>>> mapdl.post1()
>>> mapdl.k(1, 0, 0, 0)
Exception:  K is not a recognized POST1 command, abbreviation, or macro.
```

Ignore these messages by setting `ignore_errors=True`.

```python
>>> mapdl.ignore_errors = True
2020-06-08 21:39:58,094 [INFO] : K is not a
recognized POST1 command, abbreviation, or macro.  This
command will be ignored.
```


````