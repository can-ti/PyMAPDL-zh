# Setup
这些 DATABASE 命令可以用来初始化数据库、将其保存到文件中，或者用标题和单位系统对其进行注释。

```{table} Setup commands
:name: setup

| | |
|---|---|
| `**Mapdl.clear(*args,**kwargs)**` | 清空数据库。 |
| `**Mapdl.resume([fname,ext,nopar,knoplot])**` | 从数据库文件恢复数据库。 |
| `**Mapdl.save([fname,ext,slab])**` | 保存所有当前数据库信息。 |
| `**Mapdl.smbc([model])**` | Controls the display of solid model boundary condition symbols and labels. 控制实体模型边界条件符号和标签的显示。|
| `**Mapdl.stat(**kwargs)**` | Displays the status of database settings. 显示数据库设置的状态。 |
| `**Mapdl.stitle([nline,title])**` | Defines subtitles. 定义子标题。 |
| `**Mapdl.title([title])**` | Defines a main title. 定义主标题。 |
| `**Mapdl.units([label,lenfact,massfact,...])**` | Annotates the database with the system of units used. 用所使用的单位系统对数据库进行注释。 |

```

