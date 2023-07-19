# aslv

```{py:method} Mapdl.aslv(type_='', **kwargs)

Selects those areas contained in the selected volumes.\
选择那些包含在所选 volumes 中的 areas。

APDL Command: `ASLV`

Parameters:
----------

  *type_*
  : Label identifying the type of area select:
  - S - Select a new set (default).
  - R - Reselect a set from the current set.
  - A - Additionally select a set and extend the current set.
  - U - Unselect a set from the current set.

Notes
------

This command is valid in any processor.