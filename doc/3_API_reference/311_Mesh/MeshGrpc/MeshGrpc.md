# MeshGrpc

````{class} ansys.mapdl.core.mesh_grpc.MeshGrpc(mapdl)

Provides an interface to the gRPC mesh from MAPDL.\
为 MAPDL 的 gRPC 网格提供接口。

Methods
----------

```{table}

| | | |
|---|---|---|
| {doc}`MeshGrpc.nodes_in_coordinate_system(CS_id) <../MeshGrpc/nodes_in_coordinate_system>` | Return nodes in the desired coordinate system. | 返回所需坐标系中的节点。|
| {doc}`MeshGrpc.save(filename[, binary, ...]) <../MeshGrpc/save>` | Save the geometry as a vtk file | 将几何图形保存为 vtk 文件 |

```

Attribute
---------

```{table}

| | | |
|---|---|---|
| {doc}`MeshGrpc.ekey <../MeshGrpc/ekey>` | Element type key | 单元类型值 |
| {doc}`MeshGrpc.elem <../MeshGrpc/elem>` | List of elements containing raw ansys information. | 包含原始 ansys 信息的单元列表。 |
| {doc}`MeshGrpc.elem_real_constant <../MeshGrpc/elem_real_constant>` | Real constant reference for each element. | 每个单元的实常数参考值。 |
| {doc}`MeshGrpc.element_components <../MeshGrpc/element_components>` | Element components for the archive. | |
| {doc}`MeshGrpc.element_coord_system <../MeshGrpc/element_coord_system>` | Element coordinate system number | 单元坐标系编号 |
| {doc}`MeshGrpc.enum <../MeshGrpc/enum>` | Element numbers of currently selected elements | 当前选定单元的单元编号 |
| {doc}`MeshGrpc.enum_all <../MeshGrpc/enum_all>` | Array of all element numbers, even those not selected. | 所有单元编号的数组，包括未被选中的单元编号。 |
| {doc}`MeshGrpc.et_id <../MeshGrpc/et_id>` | Element type id (ET) for each element. | 每个单元的单元类型 ID (ET)。 |
| {doc}`MeshGrpc.etype <../MeshGrpc/etype>` | Element type of each element. | 每个单元的单元类型。 |
| {doc}`MeshGrpc.grid <../MeshGrpc/grid>` | VTK representation of the underlying finite element mesh. | 底层有限元网格的 VTK 表示法。 |
| {doc}`MeshGrpc.key_option <../MeshGrpc/key_option>` | Key options of selected element types. | 选定单元类型的关键选项。 |
| {doc}`MeshGrpc.local <../MeshGrpc/local>` | | |
| {doc}`MeshGrpc.material_type <../MeshGrpc/material_type>` | Material type index of each element in the archive. | 每个单元的材料类型索引。 |
| {doc}`MeshGrpc.n_elem <../MeshGrpc/n_elem>` | Number of currently selected elements in MAPDL. | MAPDL 中当前选定单元的数量。 |
| {doc}`MeshGrpc.n_node <../MeshGrpc/n_node>` | Number of currently selected nodes in MAPDL. | MAPDL 中当前选中的节点数。 |
| {doc}`MeshGrpc.nnum <../MeshGrpc/nnum>` | Array of currently selected node numbers. | 当前选择的节点编号数组。 |
| {doc}`MeshGrpc.nnum_all <../MeshGrpc/nnum_all>` | Array of all node numbers, even those not selected. | 所有节点编号的数组，包括未被选中的节点。 |
| {doc}`MeshGrpc.node_angles <../MeshGrpc/node_angles>` | Not yet implemented | 尚未实施 |
| {doc}`MeshGrpc.node_components <../MeshGrpc/node_components>` | Node components for the archive. | 节点组件。 |
| {doc}`MeshGrpc.nodes <../MeshGrpc/nodes>` | Array of nodes in Global Cartesian coordinate system. | 全局直角坐标系中的节点数组。 |
| {doc}`MeshGrpc.nodes_in_current_CS <../MeshGrpc/nodes_in_current_CS>` | Returns the nodes array in the current coordinate system. | 返回当前坐标系下的节点数组。 |
| {doc}`MeshGrpc.nodes_rotation <../MeshGrpc/nodes_rotation>` | Returns an array of node rotations | 返回节点旋转数组 |
| {doc}`MeshGrpc.rlblock <../MeshGrpc/rlblock>` | Real constant data from the RLBLOCK. | 来自 RLBLOCK 的实常数数据。 |
| {doc}`MeshGrpc.rlblock_num> <../MeshGrpc/rlblock_num>` | Indices from the real constant data | 来自实常数数据的索引 |
| {doc}`MeshGrpc.section <../MeshGrpc/section>` | Section number |  |
| {doc}`MeshGrpc.tshape <../MeshGrpc/tshape>` | Tshape of contact elements. | |
| {doc}`MeshGrpc.tshape_key <../MeshGrpc/tshape_key>` | Dict with the mapping between element type and element shape. | 包含单元类型和单元形状之间映射关系的字典。 |


```

````