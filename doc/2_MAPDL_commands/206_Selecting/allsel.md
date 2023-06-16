# allsel

````{py:method} Mapdl.allsel(labt='', entity='', **kwargs)[source]

Selects all entities with a single command.

APDL Command: `ALLSEL`

Parameters:
------------

  *labt*
  : Type of selection to be made:
    - ALL --- Selects all items of the specified entity type and all items of lower entity types (default).
    - BELOW --- Selects all items directly associated with and below the selected items of the specified entity type.

  *entity*
  : Entity type on which selection is based:
    - ALL - All entity types (default).
    - VOLU - Volumes.
    - AREA - Areas.
    - LINE - Lines.
    - KP - Keypoints.
    - ELEM - Elements.
    - NODE - Nodes.

Notes
-------

`ALLSEL` is a convenience command that allows the user to select all items of a specified entity type or to select items associated with the selected items of a higher entity.\
`ALLSEL` 是一个方便的命令，它允许用户选择指定实体类型的所有项目，或者选择与所选择的上级实体相关的项目。

An entity hierarchy is used to decide what entities will be available in the selection process. This hierarchy from top to bottom is as follows: volumes, areas, lines, keypoints, elements, and nodes. The hierarchy may also be divided into two branches: the solid model and the finite element model. The label `ALL` selects items based on one branch only, while `BELOW` uses the entire entity hierarchy. For example, `ALLSEL,ALL,VOLU` selects all volumes, areas, lines, and keypoints in the data base. `ALLSEL,BELOW,AREA` selects all lines belonging to the selected areas; all keypoints belonging to those lines; all elements belonging to those areas, lines, and keypoints; and all nodes belonging to those elements.

The `$` character should not be used after the `ALLSEL` command.

This command is valid in any processor.


Examples
--------

```py
>>> mapdl.allsel()
```


````
