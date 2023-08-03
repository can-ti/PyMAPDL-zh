# run_multiline

````{method} Mapdl.run_multiline(commands)

Run several commands as a single block

```{error} Deprecated since version 0.61.0:
This function is being deprecated. Please use `input_strings` instead.
```

Parameters:
---------

  command : *`str`*
  : Commands separated by new lines. See example.

Returns:
---------

  `str`
  : Command output from MAPDL. Includes the output from running every command, as if it was an input file.\
  MAPDL 的命令输出。包括运行每条命令的输出，如同输入文件。

Examples
---------

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
nsel,s,loc,x,0
d,all,all
nsel,s,loc,x,999,1001
type,2
esurf
esel,s,type,,2
nsle
sfe,all,3,pres,,-10
allsel
/solu
antype,0
solve
/post1
set,last
plnsol,u,sum
'''
>>> resp = mapdl.run_multiline(cmd)
>>> resp
MATERIAL          1     EX   =   200000.0
MATERIAL          1     NUXY =  0.3000000
MATERIAL          1     DENS =  0.7850000E-08
ELEMENT TYPE          1 IS SOLID186     3-D 20-NODE STRUCTURAL SOLID
 KEYOPT( 1- 6)=        0      0      0        0      0      0
 KEYOPT( 7-12)=        0      0      0        0      0      0
 KEYOPT(13-18)=        0      0      0        0      0      0
output continues...
```



````