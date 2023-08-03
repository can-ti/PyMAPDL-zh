# run_batch

````{method} LocalMapdlPool.run_batch(files, clear_at_start=True, progress_bar=True, close_when_finished=False, timeout=None, wait=True)

Run a batch of input files on the pool.\
在池上运行一批输入文件。

Parameters:
----------

  files : *`list`*
  : List of input files to run.

  clear_at_start : *`bool`* , *`optional`*
  : Clear MAPDL at the start of execution. By default this is `True`, and setting this to `False` may lead to instability.\
  在开始执行时清除 MAPDL。默认为 `True`，设置为 `False` 可能会导致不稳定。

  progress_bar : *`bool`* , *`optional`*
  : Show a progress bar when starting the pool. Defaults to `True`. Will not be shown when `wait=False`.\
  启动池时显示进度条。默认为 `True`。当 `wait=False` 时不会显示。

  close_when_finished : *`bool`* , *`optional`*
  : Exit the MAPDL instances when the pool is finished. Default `False`.\
  池结束时退出 MAPDL 实例。默认为 `False`。

  timeout : *`float`* , *`optional`*
  : Maximum runtime in seconds for each iteration. If `None`, no timeout. If specified, each iteration will be only allowed to run `timeout` seconds, and then killed and treated as a failure.\
  每次迭代的最长运行时间（秒）。如果 `None`，则无超时。如果指定，每次迭代将只允许运行 `timeout` 秒，然后被终止并视为失败。

  wait : *`bool`* , *`optional`*
  : Block execution until the batch is complete. Default `True`.\
  阻止执行，直到批处理完成。默认为 `True`。


Returns:
---------

  `list`
  : List of text outputs from MAPDL for each batch run. Not necessarily in the order of the inputs. Failed runs will not return an output. Since the returns are not necessarily in the same order as `iterable`, you may want to add some sort of tracker or note within the input files.\
  MAPDL 每次批次运行的文本输出列表。不一定按输入顺序排列。运行失败不会返回输出。由于返回的顺序不一定与 `iterable`相同，因此您可能需要在输入文件中添加某种跟踪器或注释。

Examples
--------

Run 20 verification files on the pool\
在池上运行 20 个验证文件

```python
>>> from ansys.mapdl import examples
>>> files = [examples.vmfiles['vm%d' % i] for i in range(1, 21)]
>>> outputs = pool.run_batch(files)
>>> len(outputs)
20
```




````