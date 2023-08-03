# routine

````{property} property Parameters.routine: str

Current routine string as a string. For example `'/PREP7'`.\
当前例程的字符串。例如 `'/PREP7'`

MAPDL Command: `*GET, ACTIVE, 0, ROUT`

Returns:
---------

  routine : *`str`*
  : Routine as a string. One of:
  - `"Begin level"`
  - `"PREP7"`
  - `"SOLUTION"`
  - `"POST1"`
  - `"POST26"`
  - `"AUX2"`
  - `"AUX3"`
  - `"AUX12"`
  - `"AUX15"`

Examples
------

```python
>>> mapdl.parameters.routine
'PREP7'
```


````