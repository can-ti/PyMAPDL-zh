# anstoaqwa

```{py:method} Mapdl.anstoaqwa(fname='', vertaxis='', gc='', rho='', hwl='', diffkey='', symxkey='', symykey='', **kwargs)

Creates an AQWA-LINE input file from the current ANSYS model.\
从当前 ANSYS 模型创建一个 AQWA-LINE 输入文件。

APDL Command: `ANSTOAQWA`

Parameters:
-----------

  *fname*
  : AQWA file name. Defaults to Jobname.

  *vertaxis*
  : Axis in the vertical direction:\
  Y (or 2) - Global Y axis.\
  Z (or 3) - Global Z axis (default).

  *gc*
  : Gravitational acceleration. Defaults to 9.81.

  *rho*
  : Density of water. Defaults to 1025.0.

  *hwl*
  : Waterline height in model coordinates. Defaults to 0.0.

  *diffkey*
  : Diffracting model key:\
  0 - Create a non-diffracting AQWA model.\
  1 - Create a diffracting AQWA model (default).

  *symxkey*
  : Key indicating if model is symmetric about the global XZ plane:\
  0 - No symmetry about XZ plane (default).\
  1 - Use symmetry about XZ plane. Only include (or select) half the model.

  *symkey*
  : Key indicating if model is symmetric about the global YZ plane:\
  0 - No symmetry about YZ plane (default).\
  1 - Use symmetry about YZ plane. Only include (or select) half the model.


Notes
---------

This command creates the input file Fname.aqwa for the ANSYS Aqwa Multi-Body Hydrodynamics System for diffraction analysis in AQWA-LINE from the model currently in the database, based on the currently selected set of elements. The selected set must only include the hull envelope; no internal structure should be selected.\
这条命令是根据当前数据库中的模型，基于当前选择的单元集，为 ANSYS Aqwa 多体水动力学系统在 AQWA-LINE 中进行衍射分析创建输入文件 Fname.aqwa。选定的单元集必须只包括船体包络，不应选择内部结构。

There should be a line of nodes defined at the waterline. Only those elements that are entirely below the waterline will be specified as diffracting. If there are no waterline nodes, there will be no diffracting elements at the waterline, which will severely reduce the accuracy of the diffraction analysis.

The translator maps PLANE42, SHELL41, SHELL63, and SHELL181 elements to PANELs, and maps PIPE16 and PIPE59 elements to TUBEs. It does not recognize any other element types. Any material or geometric properties can be used for the shell elements, as AQWA does not need any properties at all and the command does not use them. All the shell elements below the water must have their normals pointing outward.

TUBE elements in AQWA have material density, outside diameter, wall thickness, added mass, and drag coefficients, so appropriate properties should be used in the ANSYS model. PIPE59 elements can have added mass and damping coefficients; these will be written to the file. The ANSYS program uses the inertia coefficient CM, whereas AQWA uses the added mass coefficient CA, where CM = (1 + CA). This correction is made automatically.

In AQWA the vertical axis is always the Z-axis. The command can convert a model built with either the Y or Z-axis vertical, but the X-axis must be horizontal and should preferably be along the fore/aft axis of the vessel. If the structure is symmetric and you wish to use the symmetry options, you must only select one half or one quarter of the model, as appropriate. If you model a complete vessel and specify X symmetry, the AQWA model will contain two sets of coincident elements.

If you are working from a model created for a structural analysis, it will probably be necessary to remesh the model as the structural mesh is most likely finer than needed for a diffraction analysis.

If you enter this command interactively (with the GUI active) and no data is provided for the command options, you will be prompted for their values.

You must verify the completeness and accuracy of the data written.

```