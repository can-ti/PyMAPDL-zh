# info

````{py:method} DbNodes.info(inod, ikey)

Get information about a node.

Parameters:
----------

  *inod*: *`int`*
  : Node number. Should be 0 for key=11 for the following:
  - `DB_NUMDEFINED`
  - `DB_NUMSELECTED`
  - `DB_MAXDEFINED`
  - `DB_MAXRECLENG`

  *ikey*: *`int`*
  : Key of the information needed about the node. One of the following:
  - DB_SELECTED : return select status
    - 0 - node is undefined.
    - -1 - node is unselected.
    - 1 - node is selected.
  - DB_NUMDEFINED - return number of defined nodes
  - DB_NUMSELECTED - return number of selected nodes
  - DB_MAXDEFINED - return highest node number defined
  - DB_MAXRECLENG - return maximum record length (dp words)
  - 2 - length (dp words)
  - 3 -
  - 4 - pointer to first data word
  - 11 - return void percent (integer)
  - 17 - pointer to start of index
  - 117 - return the maximum number of DP contact data stored   - for any element
  - -1 -
  - -2 - supernode flag
  - -3 - master dof bit pattern
  - -4 - active dof bit pattern
  - -5 - solid model attachment
  - -6 - pack nodal line parametric value
  - -7 - constraint bit pattern
  - -8 - force bit pattern
  - -9 - body force bit pattern
  - -10 - internal node flag
  - -11 - orientation node flag =1 is =0 isnot
  - -11 - contact node flag <0
  - -12 - constraint bit pattern (for DSYM)
  - -13 - if dof constraint written to file. (for LSDYNA only)
  - -14 - nodal coordinate system number (set by NROTATE)
  - -101 - pointer to node data record
  - -102 - pointer to angle record
  - -103 -
  - -104 - pointer to attached couplings
  - -105 - pointer to attacted constraint equations
  - -106 - pointer to nodal stresses
  - -107 - pointer to specified disp’S
  - -108 - pointer to specified forces
  - -109 - pointer to x/y/z record
  - -110 -
  - -111 -
  - -112 - pointer to nodal temperatures
  - -113 - pointer to nodal heat generations
  - -114 -
  - -115 - pointer to calculated displacements
  - -116 -

Returns:
--------

  `int`
  : The returned value of is based on the value of `ikey`.

Examples:
---------

Query if an node is selected.

```python

>>> from ansys.mapdl.core.database import DBDef
>>> nodes = mapdl.db.nodes
>>> nodes.info(1, DBDef.DB_SELECTED)
1

```


````

