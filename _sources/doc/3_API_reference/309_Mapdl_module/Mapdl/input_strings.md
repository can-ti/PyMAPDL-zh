# input_strings

````{method} Mapdl.input_strings(commands)

Run several commands as a single block.\
将多个命令作为一个程序块运行。

These commands are all in a single string or in list of strings.\
这些命令都以单个字符串或字符串列表的形式出现。

Parameters:
----------

  commands : *`str`* or *`list` of `str`*
  : Commands separated by new lines, or a list of commands strings. See example.\
  以‘新行’隔开的命令，或命令字符串列表。请参阅示例。

Returns:
-------

  `str`
  : Command output from MAPDL. Includes the output from running every command, as if it was an input file.\
  MAPDL 的命令输出。包括运行每条命令的输出，如同输入文件。

Examples
-----------

Run several commands from Python multi-line string.

```python
>>> cmd = '''/prep7
! Mat
MP,EX,1,200000
MP,NUXY,1,0.3
MP,DENS,1,7.85e-09
! Elements
et,1,186
et,2,154
! Geometry
BLC4,0,0,1000,100,10
! Mesh
esize,5
vmesh,all
'''
>>> resp = mapdl.input_strings(cmd)
>>> resp
MATERIAL          1     EX   =   200000.0
MATERIAL          1     NUXY =  0.3000000
MATERIAL          1     DENS =  0.7850000E-08
ELEMENT TYPE          1 IS SOLID186     3-D 20-NODE STRUCTURAL SOLID
 KEYOPT( 1- 6)=        0      0      0        0      0      0
 KEYOPT( 7-12)=        0      0      0        0      0      0
 KEYOPT(13-18)=        0      0      0        0      0      0
```



````