# exit

```{py:method} Mapdl.exit(save=False, force=False)

退出 MAPDL。

Parameters:
---------------

  *sace*: *`bool`*, *`optional`*
  : 退出时保存数据库。默认为`False`。

  *force*: *`bool`*, *`optional`*
  : 覆盖任何可能抑制退出 MAPDL 的环境变量。

Notes
-----------------

如果 `PYMAPDL_START_INSTANCE` 被设置为 `False`（通常在远程测试或文档构建中设置），那么这将被忽略。用 `force=True' 来覆盖这一行为，以便总是强制退出 MAPDL，不管你的本地环境如何。

Examples
--------------

```py
>>> mapdl.exit()
```

--------------

```{py:method} Mapdl.exit(save=False, force=False)

Exit MAPDL.

Parameters:
---------------

  *sace*: *`bool`*, *`optional`*
  : Save the database on exit. Default `False`.

  *force*: *`bool`*, *`optional`*
  : Override any environment variables that may inhibit exiting MAPDL.

Notes
-----------------

If `PYMAPDL_START_INSTANCE` is set to `False` (generally set in remote testing or documentation build), then this will be ignored. Override this behavior with `force=True` to always force exiting MAPDL regardless of your local environment.

Examples
--------------

```py
>>> mapdl.exit()
```

