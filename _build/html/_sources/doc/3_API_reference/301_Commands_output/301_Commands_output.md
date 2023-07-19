# Commands output

各种 PyMAPDL 类和命令，有助于的数据后处理。

所有这些类都是 `str` 类的子类，因此它们继承了 `string` 的所有方法和属性。

```{class} ansys.mapdl.core.commands.CommandListingOutput(content, cmd=None, magicwords=None, columns_names=None)

允许将命令输出转换为本地 Python 类型。

用于处理命令的自定义类，其输出可转换为列表、Numpy 数组或 Pandas DataFrame。

该类是 python `str` 的子类，因此具有 python 字符串对象的所有方法。

此外，它还提供以下方法：

- `to_list()`
- `to_array()`
- `to_dataframe()`

```

```{csv-table}

"`CommandListingOutput.to_list()`","将命令输出为一个或多个列表。"
"`CommandListingOutput.to_array()`,"将命令输出为一个 numpy 数组。"
"`CommandListingOutput.to_dataframe([data,...])`","将命令输出为一个 Pandas DataFrame。"

```

```{class} ansys.mapdl.core.commands.BoundaryConditionsListingOutput(content, cmd=None, magicwords=None, columns_names=None)

允许将命令输出转换为本地Python类型。

自定义类，用于处理边界条件列表命令，其输出可转换为 Lists 或 Pandas DataFrame。

该类是 python `str` 的子类，因此具有 python 字符串对象的所有方法。

此外，它还提供以下方法：

- `to_list()`
- `to_dataframe()`

```

```{csv-table}

"`BoundaryConditionsListingOutput.to_list()`","将命令输出为一个或多个列表。"
"`BoundaryConditionsListingOutput.to_dataframe()`","将命令输出转换为 Pandas DaraFrame。"

```
