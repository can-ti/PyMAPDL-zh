# Selecting

These DATABASE commands are used to select subsets of database entities for further operations.\
这些 DATABASE 命令用于选择数据库实体的子集以进行进一步的操作。

```{table} Selecting commands
:name: selecting

| | |
|---|---|
| {doc}`Mapdl.allsel([labt, entity]) <../206_Selecting/allsel>` | Selects all entities with a single command. |
| {doc}`Mapdl.asll([type_, arkey])  <../206_Selecting/asll>` | Selects those areas containing the selected lines. |
| {doc}`Mapdl.asel([type_, item, comp, vmin, vmax,...])  <../206_Selecting/asel>` | Selects a subset of areas. |
| {doc}`Mapdl.aslv([type_])  <../206_Selecting/aslv>` | Selects those areas contained in the selected volumes. |
| {doc}`Mapdl.dofsel([type_, dof1, dof2, dof3,...])  <../206_Selecting/dofsel>` | Selects a DOF label set for reference by other commands. |
| {doc}`Mapdl.esel([type_, item, comp, vmin, vmax,...])  <../206_Selecting/esel>` | Selects a subset of elements. |
| {doc}`Mapdl.esla([type_])  <../206_Selecting/esla>` | Selects those elements associated with the selected areas. |
| {doc}`Mapdl.esll([type_])  <../206_Selecting/esll>` | Selects those elements associated with the selected lines. |
| {doc}`Mapdl.esln([type_, ekey, nodetype])  <../206_Selecting/esln>` | Selects those elements attached to the selected nodes. |
| {doc}`Mapdl.eslv([type_])  <../206_Selecting/eslv>` | Selects elements associated with the selected volumes. |
| {doc}`Mapdl.ksel([type_, item, comp, vmin, vmax,...])  <../206_Selecting/ksel>` | Selects a subset of keypoints or hard points. |
| {doc}`Mapdl.ksll([type_])  <../206_Selecting/ksll>` | Selects those keypoints contained in the selected lines. |
| {doc}`Mapdl.ksln([type_])  <../206_Selecting/ksln>` | Selects those keypoints associated with the selected nodes. |
| {doc}`Mapdl.lsel([type_, item, comp, vmin, vmax,...])  <../206_Selecting/lsel>` | Selects a subset of lines. |
| {doc}`Mapdl.lsla([type_])  <../206_Selecting/lsla>` | Selects those lines contained in the selected areas. |
| {doc}`Mapdl.lslk([type_, lskey])  <../206_Selecting/lslk>` | Selects those lines containing the selected keypoints. |
| {doc}`Mapdl.nsel([type_, item, comp, vmin, vmax,...])  <../206_Selecting/nsel>` | Selects a subset of nodes. |
| {doc}`Mapdl.nsla([type_, nkey])  <../206_Selecting/nsla>` | Selects those nodes associated with the selected areas. |
| {doc}`Mapdl.nsle([type_, nodetype, num])  <../206_Selecting/nsle>` | Selects those nodes attached to the selected elements. |
| {doc}`Mapdl.nslk([type_])  <../206_Selecting/nslk>` | Selects those nodes associated with the selected keypoints. |
| {doc}`Mapdl.nsll([type_, nkey])  <../206_Selecting/nsll>` | Selects those nodes associated with the selected lines. |
| {doc}`Mapdl.nslv([type_, nkey])  <../206_Selecting/nslv>` | Selects those nodes associated with the selected volumes. |
| {doc}`Mapdl.partsel([type_, pmin, pmax, pinc])  <../206_Selecting/partsel>` | Selects a subset of parts in an explicit dynamic analysis. |
| {doc}`Mapdl.vsel([type_, item, comp, vmin, vmax,...])  <../206_Selecting/vsel>` | Selects a subset of volumes. |
| {doc}`Mapdl.vsla([type_, vlkey])  <../206_Selecting/vsla>` | Selects those volumes containing the selected areas. |

```