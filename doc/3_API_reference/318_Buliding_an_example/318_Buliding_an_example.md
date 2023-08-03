# Building an example

To run the documentation, you need to have the correct versions of each tool. To do so, execute the following instruction.\
要运行文档，您需要每个工具的正确版本。为此，请执行以下指令。

```
pip install -r requirements/requirements_docs.txt
```

The Sphinx configuration is in the file [conf.py](https://github.com/pyansys/pymapdl/blob/main/doc/source/conf.py) in `doc/source`.\
Sphinx 配置文件在 `doc/source` 中的 [conf.py](https://github.com/pyansys/pymapdl/blob/main/doc/source/conf.py) 中。

To run the sphinx tool:\
运行 sphinx 工具

```
doc\make.bat html
```

There are three types of examples: dynamic, static, and semi-static.\
有三种类型的示例：动态、静态和半静态。

- Dynamic examples
- Static examples
- Semi-dynamic examples

## Dynamic examples

The dynamic examples are based on Python files and must be able to run in under three minutes.\
动态示例基于 Python 文件，必须能在三分钟内运行。

They are in the [examples](https://github.com/pyansys/pymapdl/tree/main/examples) directory in this repository.\
它们位于该版本库的 [examples](https://github.com/pyansys/pymapdl/tree/main/examples) 目录中。

Example: [2d_plate_with_a_hole.py](https://github.com/pyansys/pymapdl/blob/main/examples/00-mapdl-examples/2d_plate_with_a_hole.py) .. vale on

Here is a link to this dynamic example: {doc}`MAPDL_2D_Plane_Stress_Concentration_Analysis <../401_Full_examples_using_PyMAPDL/401_1>`.\
下面是这个动态示例的链接：{doc}`MAPDL_2D_Plane_Stress_Concentration_Analysis<.../401_Full_examples_using_PyMAPDL/401_1>`。

When an example is executed, **Total running time of the script** appears at the end of the document.\
执行示例时，**脚本总运行时间** 会出现在文件末尾。

## Static examples

Static examples are based on RST files and are not executed.\
静态示例基于 RST 文件，不会被执行。

They are in the [docsource](https://github.com/pyansys/pymapdl/tree/main/doc/source) directory. .. vale off

Example: [krylov_example.rst](https://raw.githubusercontent.com/pyansys/pymapdl/main/doc/source/examples/extended_examples/Krylov/krylov_example.rst) .. vale on

Here is a link to this static example: [Harmonic analysis using the frequency-sweep Krylov method](https://dev.mapdl.docs.pyansys.com/version/stable/examples/extended_examples/Krylov/krylov_example.html)


## Semi-dynamic examples

Semi-dynamic examples are RST files that execute Python code using this RST directive:\
半动态示例是使用该 RST 指令执行 Python 代码的 RST 文件：

```
.. jupyter-execute::
:hide-code:
```

Example: [tecfricstir.rst](https://raw.githubusercontent.com/pyansys/pymapdl-examples/main/doc/source/technology_showcase_examples/techdemo-28/ex_28-tecfricstir.rst) .. vale on

Here is a link to this semi-dynamic example: [Friction Stir Welding (FSW) Simulation](https://examples.mapdl.docs.pyansys.com/version/stable/technology_showcase_examples/techdemo-28/ex_28-tecfricstir.html)

# Recommendations

As dynamic examples must run each time documentation is built, make sure that they are very short. To get around the problem of execution time, feel free to use static or semi-static examples.\
由于动态示例必须在每次构建文档时运行，因此要确保它们非常简短。要解决执行时间的问题，可以使用静态或半静态示例。
