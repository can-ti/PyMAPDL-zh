# esln

```{py:method} Mapdl.esln(type_='', ekey='', nodetype='', **kwargs)

Selects those elements attached to the selected nodes.

APDL Command: `ESLN`

Parameters:
-------------

  *type_*
  : Label identifying the type of element selected:
  - S - Select a new set (default).
  - R - Reselect a set from the current set.
  - A - Additionally select a set and extend the current set.
  - U - Unselect a set from the current set.

  *ekey*
  : Node set key:
  - 0 - Select element if any of its nodes are in the selected nodal set (default).
  - 1 - Select element only if all of its nodes are in the selected nodal set.

  *nodetype*
  : Label identifying type of nodes to consider when selecting:
  - ALL - Select elements considering all of their nodes (default).
  - ACTIVE - Select elements considering only their active nodes. An active node is a node that contributes DOFs to the model.
  - INACTIVE - Select elements considering only their inactive nodes (such as orientation or radiation nodes).
  - CORNER - Select elements considering only their corner nodes.
  - MID - Select elements considering only their midside nodes.

Return type:
-------------

`Optional`[`str`]

Notes
--------

`ESLN` selects elements which have any (or all *EKEY*) *NodeType* nodes in the currently-selected set of nodes. Only elements having nodes in the currently-selected set can be selected.\
`ESLN` 选择在当前选择的节点集中有任何（或所有 *EKEY*）*NodeType* 节点的元素。只有在当前选择的节点集中有节点的元素才能被选中。

This command is valid in any processor.

```