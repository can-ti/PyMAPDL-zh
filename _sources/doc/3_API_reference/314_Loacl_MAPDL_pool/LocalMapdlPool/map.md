# map

````{method} LocalMapdlPool.map(func, iterable=None, progress_bar=True, close_when_finished=False, timeout=None, wait=True)

Run a function for each instance of mapdl within the pool.

Parameters:
---------

  func : *`function`*
  : User function with an instance of `mapdl` as the first argument. The remaining arguments should match the number of items in each iterable (if any).\
  用户函数，第一个参数是 `mapdl` 实例。其余参数应与每个可迭代表中的项目数（如果有）相匹配。

  iterable : *`list`* , *`tuple`* , *`optional`*
  : An iterable containing a set of arguments for `func`. If None, will run `func` once for each instance of mapdl.\
  可迭代参数，包含 `func` 的参数集。如果为空，将为每个 mapdl 实例运行一次 `func`。

  progress_bar : *`bool`* , *`optional`*
  : Show a progress bar when running the batch. Defaults to `True`.\
  运行批处理时显示进度条。默认为 `True`。

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
--------

  `list`
  : A list containing the return values for `func`. Failed runs will not return an output. Since the returns are not necessarily in the same order as `iterable`, you may want to add some sort of tracker to the return of your user function `func`.\
  包含 `func` 返回值的列表。运行失败不会返回输出。由于返回值的顺序不一定与 `iterable` 相同，因此您可能需要为用户函数 `func` 的返回值添加某种跟踪器。

Examples
---------

Run several input files while storing the final routine. Note how the user function to be mapped must use `mapdl` as the first argument. The function can have any number of additional arguments.\
运行多个输入文件，同时存储最终例程。注意要映射的用户函数必须使用 `mapdl` 作为第一个参数。函数可以有任意数量的附加参数。

```python
>>> completed_indices = []
>>> def func(mapdl, input_file, index):
        # input_file, index = args
        mapdl.clear()
        output = mapdl.input(input_file)
        completed_indices.append(index)
        return mapdl.parameters.routine
>>> inputs = [(examples.vmfiles['vm%d' % i], i) for i in range(1, 10)]
>>> output = pool.map(func, inputs, progress_bar=False, wait=True)
['Begin level',
 'Begin level',
 'Begin level',
 'Begin level',
 'Begin level',
 'Begin level',
 'Begin level',
 'Begin level',
 'Begin level']
```


````