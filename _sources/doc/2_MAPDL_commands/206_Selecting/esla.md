# esla

```{py:method} Mapdl.esla(type_='',**kwargs)

Selects those elements associated with the selected areas.

APDL Command: `ESLA`

Parameters:
-----------

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

Selects area elements belonging to meshed [`AMESH`], selected [`ASEL`] areas.

This command is valid in any processor.

```