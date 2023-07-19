# dofsel

```{py:method} Mapdl.dofsel(type_='', dof1='', dof2='', dof3='', dof4='', dof5='', dof6='', **kwargs)

Selects a DOF label set for reference by other commands.\
选择一个DOF标签集供其他命令参考。

APDL Command: `DOFSEL`

Parameters:
-------

  *type_*
  : Label identifying the type of select:
  - S - Select a new set of labels.
  - A - Add labels to the current set.
  - U - Unselect (remove) labels from the current set.
  - ALL - Restore the full set of labels.
  - STAT - Display the current select status.

  *dof1, dof2, dof3, … , dof6*
  : Used only with *Type* = S, A, or U. Valid lables are:
  - Structural labels: UX, UY, or UZ (displacements); U (UX, UY, and UZ) ; ROTX, ROTY, or ROTZ (rotations); ROT (ROTX, ROTY, and ROTZ); DISP (U and ROT); HDSP (Hydrostatic pressure 静水压力).\
  - Thermal labels: TEMP, TBOT, TE2, TE3, . . ., TTOP (temperature).
  - Acoustic（声学） labels: PRES (pressure); UX, UY, or UZ (displacements for FSI coupled elements).
  - Electric labels: VOLT (voltage); EMF (electromotive force drop); CURR (current).
  - Magnetic（磁学） labels: MAG (scalar magnetic potential); AZ (vector magnetic potential); A (AZ); CURR (current).
  - Structural force labels: FX, FY, or FZ (forces); F (FX, FY, and FZ); MX, MY, or MZ (moments); M (MX, MY, and MZ); FORC (F and M); DVOL (fluid mass flow rate).
  - Thermal force labels: HEAT, HBOT, HE2, HE3, . . ., HTOP (heat flow).
  - Fluid flow force label: FLOW (fluid flow).
  - Electric force labels: AMPS (current flow); CHRG (electric charge).
  - Magnetic force labels: FLUX (scalar magnetic flux); CSGZ (magnetic current segment).
  - Diffusion（扩散） labels: CONC (concentration); RATE (diffusion flow rate).

Command Default
--------------

Degree of freedom (and the corresponding force) labels are determined from the model.、
自由度（和相应的力）标签是由模型所决定的。

Notes
-----

Selects a degree of freedom label set for reference by other commands. The label set is used on certain commands where ALL is either input in the degree of freedom label field or implied. The active label set has no effect on the solution degrees of freedom. Specified labels which are not active in the model (from the `ET` or `DOF` command) are ignored. As a convenience, a set of force labels corresponding to the degree of freedom labels is also selected. For example, selecting UX also causes FX to be selected (and vice versa). The force label set is used on certain commands where ALL is input in the force label field.\
选择一个自由度标签集供其他命令参考。该标签集在某些命令中使用，在这些命令中，ALL是在自由度标签字段中输入的或隐含的。活动标签集对解的自由度没有影响。指定的标签如果在模型中不活跃（来自`ET`或`DOF`命令），则被忽略。为方便起见，与自由度标签相对应的力的标签集也被选中。例如，选择UX也会导致FX被选中（反之亦然）。该力标集用于某些在力标栏中输入ALL的命令。

This command is valid in any processor.

```