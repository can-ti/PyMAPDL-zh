# list

````{method} ansXpl.json()

List the records at the current level.

Parameters:
-----------

  nlev : *`int`*
  : Number of levels to recursively explore.\
  递归探索的层数。

Returns:
---------

  `str`
  : Listing of records from the current level.\
  列出当前级别的记录。

Examples
---------

Open a full file and list the current records.\
打开 `.full` 文件并列出当前记录。


```python
>>> xpl.open("file.full")
>>> xpl.list()
=====      ANSYS File Xplorer : List Blocks in File file.full
 ::FULL::HEADER         Size = 652  B     Total  Size =    180.297 KB
 ::FULL::DOFSBYNOD      Size = 24  B
 ::FULL::BACK           Size = 336  B
 ::FULL::STIFF::HEADER  Size = 117.316 KB
 ::FULL::RHS            Size = 1.910 KB 
 ::FULL::DIAGK          Size = 1.910 KB 
 ::FULL::SCLK           Size = 1.910 KB 
 ::FULL::MRK            Size = 984 B 
 ::FULL::NODEEXT        Size = 336 B 
 ::FULL::PCGDOFS        Size = 984 B 
 ::FULL::BCDOFS         Size = 984 B 
 ::FULL::BCVALUES       Size = 12 B
 ::FULL::MASS::HEADER   Size = 50.801 KB 
 ::FULL::DIAGM          Size = 1.910 KB 
 ::FULL::NGPH           Size = 336 B
```



````