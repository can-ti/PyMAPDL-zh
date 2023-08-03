# units

````{property} property Parameters.units: str

Units specified by /UNITS command.

Returns:
-----

  units : *`str`*
  : Active Units. One of:
  - `"None"`
  - `"USER"`
  - `"SI"`
  - `"CGS"`
  - `"BFT"`
  - `"BIN"`
  - `"MKS"`
  - `"MPA"`
  - `"uMKS"`

Examples
------

```python
>>> mapdl.parameters.units
'NONE'
```


````