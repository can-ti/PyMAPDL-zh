# asll

```{py:method} Mapdl.asll(type_='', arkey='', **kwargs)

Selects those areas containing the selected lines.\
选择包含选定 lines 的 areas。

APDL Command: `ASLL`

Parameters：
---------

  *type_*
  : Label identifying the type of area select:
    - S - Select a new set (default).
    - R - Reselect a set from the current set.
    - A - Additionally select a set and extend the current set.
    - U - Unselect a set from the current set.

  *arkey*
  : Specifies whether all contained area lines must be selected [LSEL]:
    - 0 - Select area if any of its lines are in the selected line set.
    - 1 - Select area only if all of its lines are in the selected line set.

Notes
---------

This command is valid in any processor.

```