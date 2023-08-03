# ansXpl

````{class} ansys.mapdl.core.xpl.ansXpl(mapdl)

ANSYS database explorer.\
ANSYS 数据库资源管理器

Examples
--------

```python
>>> from ansys.mapdl.core import launch_mapdl
>>> mapdl = launch_mapdl()
>>> xpl = mapdl.xpl
```

Open a mode file and extract a vector.\
打开一个模态文件并提取一个矢量。

```python
>>> xpl.open('file.mode')
>>> vec = xpl.read('MASS')
>>> vec.asarray()
array([ 4,  7, 10, 13, 16, 19, 22, 25, 28, 31, 34, 37, 40, 43,
        46, 49, 52, 55, 58,  1], dtype=int32)
```

Methods
--------


```{table}

| | | |
|---|---|---|
| {doc}`ansXpl.close() <../ansXpl/close>` | Close the MAPDL file after opening. | 打开后关闭 MAPDL 文件。 |
| {doc}`ansXpl.copy(newfile[, option]) <../ansXpl/copy>` | Copy the current opened as a new file. | 将当前打开的文件复制为新文件。 |
| {doc}`ansXpl.extract(recordname[, sets, asarray]) <../ansXpl/extract>` | Import a Matrix/Vector from a MAPDL result file. | 从 MAPDL 结果文件导入矩阵/矢量。 |
| {doc}`ansXpl.goto(path) <../ansXpl/goto>` | Go directly to a new location in the file. | 直接转到文件中的新位置。 |
| {doc}`ansXpl.help() <../ansXpl/help>` | XPL help message. | XPL 帮助信息。 |
| {doc}`ansXpl.info(recname[, option]) <../ansXpl/info>` | Gives details on a specific record, or all records (using "*") | 提供特定记录或所有记录的详细信息（使用 "*"）。 |
| {doc}`ansXpl.json() <../ansXpl/json>` | Return a JSON representation of the tree or records. | 返回树或记录的 JSON 表示形式。 |
| {doc}`ansXpl.list([nlev]) <../ansXpl/list>` | List the records at the current level. | 列出当前级别的记录。 |
| {doc}`ansXpl.open(filename[, option]) <../ansXpl/open>` | Open an MAPDL file to explore. | 打开 MAPDL 文件进行浏览。 |
| {doc}`ansXpl.print(recname) <../ansXpl/print>` | Print values of a given records, or all records (using "*"). | 打印指定记录或所有记录（使用 "*"）的值。 |
| {doc}`ansXpl.read(recordname[, asarray]) <../ansXpl/read>` | Read a record and return either an APDL math matrix or an APDL math vector. | 读取记录并返回 APDL 矩阵或 APDL 向量。 |
| {doc}`ansXpl.save() <../ansXpl/save>` | Save the current file, ignoring the marked records. | 保存当前文件，忽略标记的记录。 |
| {doc}`ansXpl.step(where) <../ansXpl/step>` | Go down in the tree of records |  |
| {doc}`ansXpl.up([nlev]) <../ansXpl/up>` | Go up in the tree. |  |
| {doc}`ansXpl.where() <../ansXpl/where>` | Returns the current location in the MAPDL file. | 返回 MAPDL 文件中的当前位置。 |
| {doc}`ansXpl.write(recordname, vecname) <../ansXpl/write>` | Write a given record back to an MAPDL file. | 将给定记录写回 MAPDL 文件。 |

```



````