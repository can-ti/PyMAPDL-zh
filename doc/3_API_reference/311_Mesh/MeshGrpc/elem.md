# elem

````{property} property MeshGrpc.elem

List of elements containing raw ansys information.\
包含原始 ansys 信息的单元列表。

Each element contains 10 items plus the nodes belonging to the element. The first 10 items are:\
每个单元包含 10 个 items 以及属于该单元的节点。前 10 个 items 是:

- FIELD 0 : material reference number 材料编号
- FIELD 1 : element type number 单元类型编号
- FIELD 2 : real constant reference number 实常数编号
- FIELD 3 : section number 截面编号
- FIELD 4 : element coordinate system 单元坐标系编号
- FIELD 5 : death flag (0 - alive, 1 - dead) 生死标志（0 - 活，1 - 死）
- FIELD 6 : solid model reference 实体模型参考
- FIELD 7 : coded shape key 编码形状键
- FIELD 8 : element number  单元树木
- FIELD 9 : base element number (applicable to reinforcing elements only)
- FIELDS 10 - 30 : The nodes belonging to the element in ANSYS numbering. 属于 ANSYS 编号单元的节点。




````