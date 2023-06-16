# Files

{numref}`files` 这些 SESSION 命令用于文件操作，例如删除、复制和列表。

```{table} Files commands
:name: files

| | |
|---|---|
| `**Mapdl.anatoaqwa([fname,vertaxis,gc,rho,...])**` | 从当前的 ANSYS 模型创建一个 AQWA-LINE 输入文件。|
| `**Mapdl.anstoasas([fname,key])**` | 从当前的 ANSYS 模型创建 ASAS 输入文件。 |
| `**Mapdl.assign([ident,fname,ext,lgkey])**` | 将文件名重新分配给 ANSYS 文件标识符。 |
| `**Mapdl.copy([fname1,ext1,fname2,ext2,distkey])**` | 复制文件。 |
| `**Mapdl.slashdelete([fname,ext,diskey])**` | 删除文件。 |
| `**Mapdl.fcomp([ident,level])**` | 指定文件压缩级别。 |
| `**Mapdl.lgwrite([fname,ext,kedit,...])**` | 将数据库命令日志写入文件。 |
| `**Mapdl.starlist([fname,ext])**` | 显示外部编码文件的内容。 |
| `**Mapdl.slashclog([fname,ext])**` | APDL命令:/CLOG |
| `**Mapdl.slashfdele([ident,stat])**` | 在一个二进制文件被使用后将其删除。 |
| `**Mapdl.rename([fname,ext1,fname2,ext2,...])**` | 重命名文件。 |

```

