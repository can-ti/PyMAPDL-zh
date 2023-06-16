# Setup
这些 DATABASE 命令可以用来初始化数据库、将其保存到文件中，或者用标题和单位系统对其进行注释。

```{table} Setup commands
:name: setup

| | | |
|---|---|---|
| {doc}`Mapdl.clear(*args,**kwargs) <../205_Setup/clear>` |Clear the database.| 清空数据库。 |
| {doc}`Mapdl.resume([fname,ext,nopar,knoplot]) <../205_Setup/resume>` |Resumes the database from the database file.| 从数据库文件恢复数据库。 |
| {doc}`Mapdl.save([fname,ext,slab]) <../205_Setup/save>` |Saves all current database information.| 保存所有当前数据库信息。 |
| {doc}`Mapdl.smbc([model]) <../205_Setup/smbc>` | Controls the display of solid model boundary condition symbols and labels.| 控制实体模型边界条件符号和标签的显示。|
| {doc}`Mapdl.stat(**kwargs) <../205_Setup/stat>` | Displays the status of database settings.| 显示数据库设置的状态。 |
| {doc}`Mapdl.stitle([nline,title]) <../205_Setup/stitle>` | Defines subtitles. |定义子标题。 |
| {doc}`Mapdl.title([title]) <../205_Setup/title>` | Defines a main title. |定义主标题。 |
| {doc}`Mapdl.units([label,lenfact,massfact,...]) <../205_Setup/units>` | Annotates the database with the system of units used.| 用所使用的单位系统对数据库进行注释。 |

```

