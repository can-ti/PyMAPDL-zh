# esll

```{py:method} Mapdl.esll(type_='', **kwargs)

Selects those elements associated with the selected lines.

APDL Command: `ESLL`

Parameters:
------------

  *type_*
  : Label identifying the type of element select:
  - S - Select a new set (default).
  - R - Reselect a set from the current set.
  - A - Additionally select a set and extend the current set.
  - U - Unselect a set from the current set.

Return type:
-----------

`Optional`[`str`]

Notes
------
Selects line elements belonging to meshed [`LMESH`], selected [`LSEL`] lines.

This command is valid in any processor.


```