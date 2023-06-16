# asel

````{py:method} Mapdl.asel(type_='', item='', comp='', vmin='', vmax='', vinc='', kswp='', **kwargs)

Selects a subset of areas.

APDL Command: `ASEL`

Parameters:
------------

  *type_*
  : Label identifying the type of select:
    - S - Select a new set (default)
    - R - Reselect a set from the current set.
    - A - Additionally select a set and extend the current set.
    - U - Unselect a set from the current set.
    - ALL - Restore the full set.
    - NONE - Unselect the full set.
    - INVE - Invert the current set (selected becomes unselected and vice versa).
    - STAT - Display the current select status.

  *The following fields are used only with Type = S, R, A, or U:*

  *Item*
  : Label identifying data. Valid item labels are shown in Table 105: ASEL - Valid Item and Component Labels (p. 185). Some items also require a component label. If Item = PICK (or simply “P”), graphical picking is enabled and all remaining command fields are ignored (valid only in the GUI). Defaults to AREA.

  *Comp*
  : Component of the item (if required). Valid component labels are shown in Table 105: ASEL - Valid Item and Component Labels (p. 185).

  *VMIN*
  : Minimum value of item range. Ranges are area numbers, coordinate values, attribute numbers, etc., as appropriate for the item. A component name (as specified on the CM (p. 338) command) may also be substituted for VMIN (VMAX and VINC are ignored). If Item = MAT, TYPE, REAL, or ESYS and if VMIN is positive, the absolute value of Item is compared against the range for selection; if VMIN is negative, the signed value of Item is compared. See the ALIST (p. 106) command for a discussion of signed attributes.

  *VMAX*
  : Maximum value of item range. VMAX defaults to VMIN.

  *VINC*
  : Value increment within range. Used only with integer ranges (such as for area numbers). Defaults to 1. VINC cannot be negative.

  *KSWP*
  : Specifies whether only areas are to be selected:
    - *kswp = 0* --- Select areas only.
    - *kswp = 1* --- Select areas, as well as keypoints, lines, nodes, and elements associated with selected areas.\
    Valid only with Type = S.

Notes
-----

Selects a subset of areas. For example, to select those areas with area numbers 1 through 7, use

```py
>>> mapdl.asel('S','AREA','',1,7)
```

The selected subset is then used when the ALL label is entered (or implied) on other commands, such as

```py
mapdl.alist('ALL')
```

Only data identified by area number are selected. Data are flagged as selected and unselected; no data are actually deleted from the database.

In a cyclic symmetry analysis, area hot spots can be modified. Consequently, the result of an area selection may be different before and after the `CYCLIC` command.

If *Item* = ACCA, the command selects only those areas that were created by concatenation. The *KSWP* field is processed, but the *Comp, VMIN, VMAX*, and *VINC* fields are ignored.\
对 *KSWP* 字段进行处理，但 *Comp、VMIN、VMAX* 和 *VINC* 字段被忽略。

This command is valid in any processor.

For Selects based on non-integer numbers (coordinates, results, etc.), items that are within the range VMIN-*Toler* and VMAX+*Toler* are selected. The default tolerance *Toler* is based on the relative values of VMIN and VMAX as follows:

- If VMIN = VMAX, *Toler* = 0.005 x VMIN.
- If VMIN = VMAX = 0.0, *Toler* = 1.0E-6.
- If VMAX ≠ VMIN, *Toler* = 1.0E-8 x (VMAX-VMIN).

Use the `SELTOL` command to override this default and specify *Toler* explicitly.

{numref}`asel` : `ASEL` - Valid Item and Component Labels

```{table} Valid Item and Component Labels `ASEL, *Type Item,Comp,VMIN,VMAX,VINC,KSWP*`
:name: asel


| Item | Comp | Description |
| --- | --- | --- |
|AREA| |Area number. |
|EXT| |Area numbers on exterior of selected volumes (ignore remaining fields). |
|LOC|X, Y, Z|X, Y, or Z center (picking "hot spot" location in the active coordinate system). |
|HPT| |Area number (selects only areas with associated hard points). |
|MAT| |Material number associated with the area. |
|TYPE| |Element type number associated with the area. |
|REAL| |Real constant set number associated with the area. |
|ESYS| |Element coordinate system associated with the area. |
|SECN| |Section number associated with the area. |
|ACCA| |Concatenated areas (selects only areas that were created by area concatenation [`ACCAT`]). |


Examples
------------

Select area(s) at location x == 0. Note that value of seltol is used since `vmin == vmax`.

```py
>>> mapdl.asel('s','loc','x',0)
```

Select areas between `y == 2` and `y == 4`

```py
>>> mapdl.asel('S','LOC','Y',2,4)
```

````