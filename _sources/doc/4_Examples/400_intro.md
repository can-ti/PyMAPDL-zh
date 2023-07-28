 # Examples

下面是一系列使用 MAPDL 和 `ansys-MAPDL-core` 库的示例。

## 使用 PyMAPDL 的完整示例

这些示例演示了使用 PyMAPDL 模块的完整示例。

::::{grid} 1 1 2 3
:class-container: text-center
:gutter: 3

:::{grid-item-card}
:link: content/myst
:link-type: doc
:class-header: bg-light

MAPDL 2D Plane Stress Concentration Analysis 🚀
^^^

本例展示了如何使用 PyMAPDL 确定和验证 "应力集中系数"，先使用二维平面单元建模，然后使用三维单元进行验证。

:::

:::{grid-item-card}
:link: content/myst
:link-type: doc
:class-header: bg-light

2D Pressure Vessel 🚀
^^^

本例演示如何创建一个基本的压力容器并对其施加压力。

:::

:::{grid-item-card}
:link: content/myst
:link-type: doc
:class-header: bg-light

3D Stress Concentration Analysis for a Notched Plate 🚀
^^^

本教程是二维平面示例 MAPDL 二维平面应力集中分析的三维推论，但本示例验证了在有限宽度薄板上建立相对单凹槽模型时的应力集中系数 $K-t$。

:::

:::{grid-item-card}
:link: content/myst
:link-type: doc
:class-header: bg-light

Basic Thermal Analysis with pyMAPDL 🚀
^^^

本例演示了如何使用 MAPDL 在 pyMAPDL 中创建板块、施加热边界条件、求解并绘制曲线。

:::

:::{grid-item-card}
:link: content/myst
:link-type: doc
:class-header: bg-light

3D Acoustic Analysis
^^^

本例演示了如何使用 PyMAPDL 和 FLUID 元素进行声学分析。
:::

:::{grid-item-card}
:link: content/myst
:link-type: doc
:class-header: bg-light

Basic DPF-Core Usage with PyMAPDL 🎁
^^^

本示例改编自《DPF-Core 基本使用示例》，展示了如何在 DPF 中打开结果文件并进行一些基本的后处理。
:::

:::{grid-item-card}
:link: content/myst
:link-type: doc
:class-header: bg-light

Static simulation of double cantilever beam test via cohesive elements 🚀
^^^

这个例子是经典的双悬臂梁试验，通常用于研究复合材料板的模式 I 界面分层。
:::

:::{grid-item-card}
:link: content/myst
:link-type: doc
:class-header: bg-light

Contact Element Example 🚀
^^^

本例演示如何为一般接触行为创建接触单元。
:::

:::{grid-item-card}
:link: content/myst
:link-type: doc
:class-header: bg-light

Cyclic Analysis 🚀
^^^

本示例使用循环扇形的参数几何创建了一个叶盘，然后对该循环扇形进行模态分析。然后，我们使用传统的 MAPDL reader 对结果进行后处理，最后使用参数建模器生成另一个循环模型。
:::


:::{grid-item-card}
:link: content/myst
:link-type: doc
:class-header: bg-light

Static Cyclic Analysis
^^^

在 1000 RPM 转速下，使用英制单位系统对转子扇形进行静态循环分析。
:::

:::{grid-item-card}
:link: content/myst
:link-type: doc
:class-header: bg-light

Thermal-structural analysis of exhaust manifold
^^^


本例说明如何映射 CFD 分析结果并执行有限元 (FE) 分析。
:::

:::{grid-item-card}
:link: content/myst
:link-type: doc
:class-header: bg-light

Plotting and Mesh Access 🚀
^^^

本示例演示了如何将基本几何图形加载到 MAPDL 中进行分析，并演示了如何使用内置的 Python 特定绘图功能。 
:::

:::{grid-item-card}
:link: content/myst
:link-type: doc
:class-header: bg-light

Structural Analysis of a Lathe Cutter 🚀
^^^

基本介绍 PyMAPDL 的功能。
:::

:::{grid-item-card}
:link: content/myst
:link-type: doc
:class-header: bg-light

MAPDL 3D Beam Example 🚀
^^^

这是一个简单的示例，加载包含梁的档案文件，然后使用简化的 `modal_analysis` 方法运行模态分析。 
:::

:::{grid-item-card}
:link: content/myst
:link-type: doc
:class-header: bg-light

MAPDL 2D Beam Example 🚀
^^^

本例来自 Paletikrishna Chaitanya、Sambanarajesh Kumar 和 Datti Srinivas 合著的《使用 ansys 11.0 进行有限元分析》一书。 PHI Learning Pvt. Ltd., 1 Jan 2010.
:::

:::{grid-item-card}
:link: content/myst
:link-type: doc
:class-header: bg-light

Path Operations within pyMAPDL and MAPDL 🚀
^^^

本教程展示了如何使用 pyansys 和 MAPDL 沿路径进行应力插值。其中展示了 *pyvista* 模块执行插值的一些高级功能。
:::

:::{grid-item-card}
:link: content/myst
:link-type: doc
:class-header: bg-light

Pressure Vessel 🚀
^^^

本例演示如何创建一个基本压力容器并对其施加压力。
:::

:::{grid-item-card}
:link: content/myst
:link-type: doc
:class-header: bg-light

PyVista Mesh Integration 🚀
^^^

在 MAPDL 中对 pyvista 生成的网格进行模态分析。
:::

:::{grid-item-card}
:link: content/myst
:link-type: doc
:class-header: bg-light

CFX pressure data mapping to structural blade
^^^

本测试的目的是在 PyMAPDL 中演示 CFX 压力数据与 11 叶片结构模型的映射。
:::

:::{grid-item-card}
:link: content/myst
:link-type: doc
:class-header: bg-light

Example Thermal Transient Analysis 🚀
^^^

该示例展示了如何使用 PyMAPDL 输入随时间变化的温度表来改变梁的温度。该示例使用的对流载荷具有独立变化的对流系数和体积温度。
:::
::::

## PyMAPDL math examples

这些示例演示了如何使用 PyMAPDL 库中的 APDL math。

