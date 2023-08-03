# result

````{property} property Mapdl.result

Binary interface to the result file using `ansys.mapdl.reader.rst.Result`.\
使用 `ansys.mapdl.reader.rst.Result` 连接结果文件的二进制接口。

Returns:
-------

  `ansys.mapdl.reader.rst.Result`
  : Result reader class. See [Legacy PyMAPDL Reader](https://readerdocs.pyansys.com/).


Examples
-------

```python
>>> mapdl.solve()
>>> mapdl.finish()
>>> result = mapdl.result
>>> print(result)
PyMAPDL-Reader Result file object
Units       : User Defined
Version     : 18.2
Cyclic      : False
Result Sets : 1
Nodes       : 3083
Elements    : 977
...
Available Results:
EMS : Miscellaneous summable items (normally includes face pressures)
ENF : Nodal forces
ENS : Nodal stresses
ENG : Element energies and volume
EEL : Nodal elastic strains
ETH : Nodal thermal strains (includes swelling strains)
EUL : Element euler angles
EMN : Miscellaneous nonsummable items
EPT : Nodal temperatures
NSL : Nodal displacements
RF  : Nodal reaction forces
```


````