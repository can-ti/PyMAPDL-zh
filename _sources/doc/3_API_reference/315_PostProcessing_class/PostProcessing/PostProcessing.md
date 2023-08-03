# PostProcessing

````{class} ansys.mapdl.core.post.PostProcessing(mapdl)[

Post-processing using an active MAPDL session

Examples
---------

Get all the time values after loading POST1.\
加载 POST1 后获取所有时间值。

```python
>>> mapdl.post1()
>>> mapdl.post_processing.time_values
[75.00054133588232,
 75.00081189985094,
 75.00121680412036,
 75.00574491751847,
 75.03939292229019,
 75.20949687626468]
```

Return the number of data sets in the result file.\
返回结果文件中数据集的数量。

```python
>>> mapdl.post_processing.nsets
1
```

Plot the thermal equivalent strain for the second result.\
绘制第二个结果的热等效应变。

```python
>>> mapdl.post1()
>>> mapdl.set(1, 2)
>>> mapdl.post_processing.plot_nodal_thermal_eqv_strain()
```

Nodal rotation in all dimensions for current result.\
当前结果在所有维度上的节点旋转。

```python
>>> mapdl.post1()
>>> mapdl.set(1, 1)
>>> mapdl.post_processing.nodal_rotation('ALL')
array([[0., 0., 0.],
       [0., 0., 0.],
       [0., 0., 0.],
       ...,
       [0., 0., 0.],
       [0., 0., 0.],
       [0., 0., 0.]])
```

Nodes corresponding to the nodal rotations.\
与节点旋转相对应的节点。

```python
>>> mapdl.mesh.nnum_all
array([   1,    2,    3, ..., 7215, 7216, 7217], dtype=int32)
```

Method
-------

```{table}

| | | |
|---|---|---|
| {doc}`PostProcessing.element_displacement([...]) <../Post/Processing/element_displacement>` | Return element displacement. | 返回单元位移。 |
| {doc}`PostProcessing.element_stress(component[, ...]) <../Post/Processing/element_stress>` | Return element component or principal stress. | 返回单元应力分量或主应力。 |
| {doc}`PostProcessing.element_temperature([option]) <../Post/Processing/element_temperature>` | Return element temperature. | 返回单元温度。 |
| {doc}`PostProcessing.element_values(item[, comp, ...]) <../Post/Processing/element_values>` | Compute the element-wise values for a given item and component. | 计算给定项目和组件的单元数量。 |
| {doc}`PostProcessing.nodal_component_stress(component) <../Post/Processing/nodal_component_stress>` | Nodal component stress. | 节点组件应力。 |
| {doc}`PostProcessing.nodal_contact_friction_stress() <../Post/Processing/nodal_contact_friction_stress>` | Nodal contact friction stress of the current result. | 当前结果的节点接触摩擦应力。 |
| {doc}`PostProcessing.nodal_displacement([component]) <../Post/Processing/nodal_displacement>` | Nodal X, Y, or Z structural displacement. | 节点 X、Y 或 Z 方向的结构位移。 |
| {doc}`PostProcessing.nodal_elastic_component_strain(...) <../Post/Processing/nodal_elastic_component_strain>` | Elastic nodal component strain | 节点组件弹性应变 |
| {doc}`PostProcessing.nodal_elastic_eqv_strain() <../Post/Processing/nodal_elastic_eqv_strain>` | The elastic nodal equivalent strain of the current result. | 当前结果的弹性节点等效应变。 |
| {doc}`PostProcessing.nodal_elastic_principal_strain(...) <../Post/Processing/nodal_elastic_principal_strain>` | Nodal elastic principal elastic strain. | 节点主弹性应变。 |
| {doc}`PostProcessing.nodal_elastic_strain_intensity() <../Post/Processing/nodal_elastic_strain_intensity>` | The elastic nodal strain intensity of the current result. | 当前结果的节点弹性应变强度。 |
| {doc}`PostProcessing.nodal_eqv_stress() <../Post/Processing/nodal_eqv_stress>` | The nodal equivalent stress of the current result. | 当前结果的节点等效应力。 |
| {doc}`PostProcessing.nodal_plastic_component_strain(...) <../Post/Processing/nodal_plastic_component_strain>` | Plastic nodal component strain. | 节点组件塑性应变 |
| {doc}`PostProcessing.nodal_plastic_eqv_strain() <../Post/Processing/nodal_plastic_eqv_strain>` | The plastic nodal equivalent strain of the current result. | 当前结果的节点塑性等效应变。 |
| {doc}`PostProcessing.nodal_plastic_principal_strain(...) <../Post/Processing/nodal_plastic_principal_strain>` | Nodal plastic principal plastic strain. | 节点塑性主应变 |
| {doc}`PostProcessing.nodal_plastic_strain_intensity() <../Post/Processing/nodal_plastic_strain_intensity>` | The plastic nodal strain intensity of the current result. | 当前结果的节点塑性应变强度。 |
| {doc}`PostProcessing.nodal_pressure() <../Post/Processing/nodal_pressure>` | The nodal pressure of the current result. | 当前结果的节点压力。 |
| {doc}`PostProcessing.nodal_principal_stress(component) <../Post/Processing/nodal_principal_stress>` | Nodal principal stress. | 节点主应力 |
| {doc}`PostProcessing.nodal_rotation([component]) <../Post/Processing/nodal_rotation>` | Nodal X, Y, or Z structural rotation | 节点 X、Y 或 Z 结构旋转 |
| {doc}`PostProcessing.nodal_stress_intensity() <../Post/Processing/nodal_stress_intensity>` | The nodal stress intensity of the current result. | 当前结果的节点应力强度。 |
| {doc}`PostProcessing.nodal_temperature() <../Post/Processing/nodal_temperature>` | The nodal temperature of the current result. | 当前结果的节点温度。 |
| {doc}`PostProcessing.nodal_thermal_component_strain(...) <../Post/Processing/nodal_thermal_component_strain>` | Thermal nodal component strain | 节点组件热应变 |
| {doc}`PostProcessing.nodal_thermal_eqv_strain() <../Post/Processing/nodal_thermal_eqv_strain>` | The thermal nodal equivalent strain of the current result. | 当前结果的节点等效热应变。 |
| {doc}`PostProcessing.nodal_thermal_principal_strain(...) <../Post/Processing/nodal_thermal_principal_strain>` | Nodal principal thermal strain. | 节点主热应变 |
| {doc}`PostProcessing.nodal_thermal_strain_intensity() <../Post/Processing/nodal_thermal_strain_intensity>` | The thermal nodal strain intensity of the current result. | 当前结果的节点热应变强度。 |
| {doc}`PostProcessing.nodal_total_component_strain(...) <../Post/Processing/nodal_total_component_strain>` | Total nodal component strain | 节点总应变 |
| {doc}`PostProcessing.nodal_total_eqv_strain() <../Post/Processing/nodal_total_eqv_strain>` | The total nodal equivalent strain of the current result. | 当前结果的全部节点的等效应变。 |
| {doc}`PostProcessing.nodal_total_principal_strain(...) <../Post/Processing/nodal_total_principal_strain>` | Total nodal principal strain. | 全部节点主应变 |
| {doc}`PostProcessing.nodal_total_strain_intensity() <../Post/Processing/nodal_total_strain_intensity>` | The total nodal strain intensity of the current result. | 当前结果的全部节点的应变强度。 |
| {doc}`PostProcessing.nodal_values(item[, comp]) <../Post/Processing/nodal_values>` | Obtain the nodal values for a given item and component. | 获取给定项目和组件的节点值。 |
| {doc}`PostProcessing.nodal_voltage() <../Post/Processing/nodal_voltage>` | The nodal voltage of the current result. | 当前结果的节点电压。 |
| {doc}`PostProcessing.plot_element_displacement([...]) <../Post/Processing/plot_element_displacement>` | Plot element displacement. | 绘制单元位移图。 |
| {doc}`PostProcessing.plot_element_stress(component) <../Post/Processing/plot_element_stress>` | Plot element component or principal stress. | 绘制单元应力分量或主应力。 |
| {doc}`PostProcessing.plot_element_temperature([...]) <../Post/Processing/plot_element_temperature>` | Plot element temperature | 绘制单元温度 |
| {doc}`PostProcessing.plot_element_values(item, comp) <../Post/Processing/plot_element_values>` | Plot element values. | 绘制单元值。 |
| {doc}`PostProcessing.plot_nodal_component_stress(...) <../Post/Processing/plot_nodal_component_stress>` | Plot nodal component stress. | 绘制节点组件应力图 |
| {doc}`PostProcessing.plot_nodal_contact_friction_stress([...]) <../Post/Processing/plot_nodal_contact_friction_stress>` | Plot the nodal contact friction stress of the current result. | 绘制当前结果的节点接触摩擦应力。 |
| {doc}`PostProcessing.plot_nodal_displacement([...]) <../Post/Processing/plot_nodal_displacement>` | Plot nodal displacement | 绘制节点位移图 |
| {doc}`PostProcessing.plot_nodal_elastic_component_strain(...) <../Post/Processing/plot_nodal_elastic_component_strain>` | Plot nodal elastic component strain. | 绘制节点弹性应变分量。 |
| {doc}`PostProcessing.plot_nodal_elastic_eqv_strain([...]) <../Post/Processing/plot_nodal_elastic_eqv_strain>` | Plot the elastic nodal equivalent strain of the current result. | 绘制当前结果的节点弹性等效应变。 |
| {doc}`PostProcessing.plot_nodal_elastic_principal_strain(...) <../Post/Processing/plot_nodal_elastic_principal_strain>` | Plot elastic nodal principal strain. | 绘制节点弹性主应变。 |
| {doc}`PostProcessing.plot_nodal_elastic_strain_intensity([...]) <../Post/Processing/plot_nodal_elastic_strain_intensity>` | Plot the elastic nodal strain intensity of the current result. | 绘制当前结果的节点弹性应变强度。 |
| {doc}`PostProcessing.plot_nodal_eqv_stress([...]) <../Post/Processing/plot_nodal_eqv_stress>` | Plot nodal equivalent stress of the current result. | 绘制当前结果的节点等效应力。 |
| {doc}`PostProcessing.plot_nodal_plastic_component_strain(...) <../Post/Processing/plot_nodal_plastic_component_strain>` | Plot nodal plastic component strain. | 绘制节点塑性应变分量。 |
| {doc}`PostProcessing.plot_nodal_plastic_eqv_strain([...]) <../Post/Processing/plot_nodal_plastic_eqv_strain>` | Plot the plastic nodal equivalent strain of the current result. | 绘制当前结果的节点塑性等效应变。 |
| {doc}`PostProcessing.plot_nodal_plastic_principal_strain(...) <../Post/Processing/plot_nodal_plastic_principal_strain>` | Plot plastic nodal principal strain. | 绘制节点塑性主应变。 |
| {doc}`PostProcessing.plot_nodal_plastic_strain_intensity([...]) <../Post/Processing/plot_nodal_plastic_strain_intensity>` | Plot the plastic nodal strain intensity of the current result. | 绘制当前结果的节点塑性应变强度。 |
| {doc}`PostProcessing.plot_nodal_pressure([...]) <../Post/Processing/plot_nodal_pressure>` | Plot nodal pressure of the current result. | 绘制当前结果的节点压力。 |
| {doc}`PostProcessing.plot_nodal_principal_stress(...) <../Post/Processing/plot_nodal_principal_stress>` | Plot nodal principal stress. | 绘制节点主应力图 |
| {doc}`PostProcessing.plot_nodal_rotation(component) <../Post/Processing/plot_nodal_rotation>` | Plot nodal rotation. | 绘制节点旋转图。 |
| {doc}`PostProcessing.plot_nodal_stress_intensity([...]) <../Post/Processing/plot_nodal_stress_intensity>` | Plot the nodal stress intensity of the current result. | 绘制当前结果的节点应力强度。 |
| {doc}`PostProcessing.plot_nodal_temperature([...]) <../Post/Processing/plot_nodal_temperature>` | Plot nodal temperature of the current result. | 绘制当前结果的节点温度。 |
| {doc}`PostProcessing.plot_nodal_thermal_component_strain(...) <../Post/Processing/plot_nodal_thermal_component_strain>` | Plot nodal thermal component strain. | 绘制节点热应变分量。 |
| {doc}`PostProcessing.plot_nodal_thermal_eqv_strain([...]) <../Post/Processing/plot_nodal_thermal_eqv_strain>` | Plot the thermal nodal equivalent strain of the current result. | 绘制当前结果的节点热等效应变。 |
| {doc}`PostProcessing.plot_nodal_thermal_principal_strain(...) <../Post/Processing/plot_nodal_thermal_principal_strain>` | Plot thermal nodal principal strain. | 绘制节点热主应变。 |
| {doc}`PostProcessing.plot_nodal_thermal_strain_intensity([...]) <../Post/Processing/plot_nodal_thermal_strain_intensity>` | Plot the thermal nodal strain intensity of the current result. | 绘制当前结果的节点热应变强度。 |
| {doc}`PostProcessing.plot_nodal_total_component_strain(...) <../Post/Processing/plot_nodal_total_component_strain>` | Plot nodal total component strain. | 绘制节点总应变。 |
| {doc}`PostProcessing.plot_nodal_total_eqv_strain([...]) <../Post/Processing/plot_nodal_total_eqv_strain>` | Plot the total nodal equivalent strain of the current result. | 绘制当前结果的节点等效应变。 |
| {doc}`PostProcessing.plot_nodal_total_principal_strain(...) <../Post/Processing/plot_nodal_total_principal_strain>` | Plot total nodal principal strain. | 绘制节点主应变。 |
| {doc}`PostProcessing.plot_nodal_total_strain_intensity([...]) <../Post/Processing/plot_nodal_total_strain_intensity>` | Plot the total nodal strain intensity of the current result. | 绘制当前结果的节点应变强度。 |
| {doc}`PostProcessing.plot_nodal_values(item, comp) <../Post/Processing/plot_nodal_values>` | Plot nodal values | 绘制节点值(item,comp) |
| {doc}`PostProcessing.plot_nodal_voltage([...]) <../Post/Processing/plot_nodal_voltage>` | Plot nodal voltage of the current result. | 绘制当前结果的节点电压。 |

```



Attribute
-------

```{table}

| | | |
|---|---|---|
| {doc}`PostProcessing.filename <../Post/Processing/filename>` | Return the current result file name without extension. | 返回不带扩展名的当前结果文件名。 |
| {doc}`PostProcessing.freq <../Post/Processing/freq>` | Frequency associated with current result in the database. | 与数据库中当前结果相关的频率。 |
| {doc}`PostProcessing.frequency_values <../Post/Processing/frequency_values>` | Return an array of the frequency values for all result sets. | 返回所有结果集的频率值数组。 |
| {doc}`PostProcessing.load_step <../Post/Processing/load_step>` | Current load step number | 当前的荷载步编号 |
| {doc}`PostProcessing.nsets <../Post/Processing/nsets>` | Number of data sets on result file. | 结果文件中的数据集数量。 |
| {doc}`PostProcessing.selected_elements <../Post/Processing/selected_elements>` | Mask of the selected elements. | 选定单元的掩码。 |
| {doc}`PostProcessing.selected_nodes <../Post/Processing/selected_nodes>` | Mask of the selected nodes. | 所选节点的掩码。 |
| {doc}`PostProcessing.step <../Post/Processing/step>` | Current step number | 当前的荷载步编号 |
| {doc}`PostProcessing.sub_step <../Post/Processing/sub_step>` | Current sub step number | 当前子步编号 |
| {doc}`PostProcessing.time <../Post/Processing/time>` | Time associated with current result in the database. | 与数据库中当前结果相关的 time。 |
| {doc}`PostProcessing.time_values <../Post/Processing/time_values>` | Return an array of the time values for all result sets. | 返回包含所有结果集时间值的数组 |


```


````