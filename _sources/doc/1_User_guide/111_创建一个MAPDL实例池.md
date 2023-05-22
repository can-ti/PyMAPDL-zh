# 创建一个 MAPDL 实例池
PyMAPDL 包含了 **`MapdlLocalPool`**类，以简化为批处理创建 **`Mapdl`** class 的多个本地实例。这可用于对一组输入文件的批处理、收敛分析或其他与批处理有关的过程。

下面这段代码创建了一个池(pool):

```python
>>> from ansys.mapdl.core import LocalMapdlPool
>>> pool = LocalMapdlPool(10)
'MAPDL Pool with 10 active instances'
```

你也可以在创建池时提供额外的关键字参数。例如下面这段代码创建了几个实例，每个实例分配一个 CPU，并在它们自己当前的隔离目录中运行：

```python
>>> import os
>>> my_path = os.getcmd()
>>> pool = LocalMapdlPool(10, nproc=1, run_location=my_path)
Creating Pool: 100%|########| 10/10 [00:01<00:00,  1.43it/s]
```

您可以使用以下代码访问每个 MAPDL 实例:

```python
>>> pool[0]
<ansys.mapdl.core.mapdl.MapdlGrpc object at 0x7f66270cc8d0>
```

注意，这是一个自我修复池(self-healing pool)。如果 MAPDL 的实例在批处理过程 'dies' 了，则该实例将自动重新启动。在创建池时，可以通过设置 `restart_failed=False` 来关闭此行为。

## 运行一组输入文件
你可以使用 **`run_batch`** 方法来运行一组预先生成的输入文件。例如，这段代码将运行第一组共 20 个验证文件：

```python
>>> from ansys.mapdl.core import examples
>>> files = [examples.vmfiles["vm%d" % i] for i in range(1, 21)]
>>> outputs = pool.run_batch(files)
>>> len(outputs)
20
```

## 运行一个用户函数
你可以使用池在一组输入上的每个 MAPDL 实例上运行一个自定义的用户函数。与上面 **`run_batch`** 函数的例子一样，下面的代码使用一组验证文件。然而，它是作为一个函数来实现的，并输出最后的例程，而不是 MAPDL 的文本输出。

```python
completed_indices = []


def func(mapdl, input_file, index):
    # input_file, index = args
    mapdl.clear()
    output = mapdl.input(input_file)
    completed_indices.append(index)
    return mapdl.parameters.routine


inputs = [(examples.vmfiles["vm%d" % i], i) for i in range(1, 10)]
output = pool.map(func, inputs, progress_bar=True, wait=True)
[
    "Begin level",
    "Begin level",
    "Begin level",
    "Begin level",
    "Begin level",
    "Begin level",
    "Begin level",
    "Begin level",
    "Begin level",
]
```

## API 说明
有关详细说明，请参阅[本地 MAPDL 池](https://mapdl.docs.pyansys.com/version/stable/api/pool.html#ref-pool-api)。

