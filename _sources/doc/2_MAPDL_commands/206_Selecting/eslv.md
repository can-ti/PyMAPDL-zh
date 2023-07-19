# eslv

```{py:method} Mapdl.eslv(type_='',**kwargs)

Selects elements associated with the selected volumes.

APDL Command: `ESLV`

Parameters:
-----------

  *type_*
  : Label identifying the type of element selected:
  - S - Select a new set (default).
  - R - Reselect a set from the current set.
  - A - Additionally select a set and extend the current set.
  - U - Unselect a set from the current set.

Return type:
-------------

`Optional`[`str`]

Notes
--------

Selects volume elements belonging to meshed [`VMESH`], selected [`VSEL`] volumes.

This command is valid in any processor.

```