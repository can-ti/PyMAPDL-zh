# units

```{py:method} Mapdl.units(label='', lenfact='', massfact='', timefact='', tempfact='', toffset='', chargefact='', forcefact='', heatfact='', **kwargs)

Annotates the database with the system of units used.

APDL Command: `/UNITS`

Parameters:
---------

  *label* --- Label to denote the system of units used in this job:
  : *USER* --- User-defined system (default).\
  *SI* --- International system (m, kg, s, K).\
  *MKS* --- MKS system (m, kg, s, °C).\
  *uMKS* --- μMKS system (μm, kg, s, °C).\
  *CGS* --- CGS system (cm, g, s, °C).\
  *MPA* --- MPA system (mm, Mg, s, °C).\
  *BFT* --- U. S. Customary system using feet (ft, slug, s, °F).\
  *BIN* --- U. S. Customary system using inches (in, lbf*s2/in, s, °F).

  If *Label* = *USER*, the remaining fields on this command may be used to enter conversion factors that are appropriate for the user-defined system of units.\
如果 *Label* = USER，则此命令上的其余字段可用于输入适用于用户定义的单位系统的换算系数。

  *Label* = *USER*
  : LENFACT --- Conversion factor to meter (m). Default = 1.\
  MASSFACT --- Conversion factor to kilogram (kg). Default = 1.\
  TIMEFACT --- Conversion factor to second (s). Default = 1.\
  TEMPFACT --- Conversion factor to kelvin (K). Default = 1.\
  TOFFSET --- Temperature offset from absolute zero in kelvin. Default = 0.\
  CHARGEFACT --- Conversion factor to coulomb. Default = 1.\
  FORCEFACT --- Conversion factor to newton (N). Default = 1.\
  HEATFACT —-- Conversion factor to joule (J). Default = 1.



Notes
------

Allows the user to set a marker in the database indicating the system of units used. The setting may be reviewed with the `/STATUS` command at the Begin level. The units label and conversion factors on this command are for user convenience only and have no effect on the analysis or data. That is, `/UNITS` will not convert database items from one system to another (e.g., from U.S.Customary to SI, etc.). The units setting will be written to the file of IGES data [`IGESOUT` or `CDWRITE`], which can then be read by many programs that read IGES files. The user must still use consistent units for the results to be valid.\
允许用户在数据库中设置标记，指示所使用的单位系统。可以使用 `/STATUS` 命令在“开始”级别查看该设置。此命令上的单位标签和换算系数仅为方便用户起见，对分析或数据没有影响。也就是说，`/UNITS` 不会将数据库项目从一个系统转换为另一个系统（例如，从 U.S.Customary 转换为 SI 等）。单位设置将被写入 IGES 数据文档[`IGESOUT` 或 `CDWRITE`]，然后许多读取 IGES 文档的进程可以读取该文档。用户必须仍使用一致的单位才能使结果有效。

If you choose the MKS system of units, the EPZRO option for the `EMUNIT` command is set to 8.85 e-12 F/m. (EPZRO specifies alternate free-space permittivity.)\
如果选择 MKS 单位系统，`EMUNIT` 命令的 EPZRO 选项设置为 8.85 e-12 F/m。 （EPZRO 指定备用自由空间介电常数。）

For micro-electromechanical systems (MEMS), where dimensions are on the order of microns, see the conversion factors in System of Units in the Coupled-Field Analysis Guide.\
对于尺寸为微米量级的微机电系统 （MEMS），请参阅《耦合场分析指南》中单位制的转换系数。

If you use the ANSYS ADAMS Interface to export model information to the ADAMS program, the /UNITS command is required to ensure the correct transfer of data between ANSYS and ADAMS. You may choose a predefined unit system label (Label = SI, CGS, etc.) or you can select the user- defined system option (Label = USER) and input the appropriate conversion factors (LENFACT, MASSFACT, TIMEFACT, and FORCEFACT). The conversion factors will be written to the ADAMS input file Jobname.MNF in order to correctly generate the load. For more information, see Export to ADAMS in the Substructuring Analysis Guide.\
如果使用 ANSYS ADAMS 接口将模型信息导出到 ADAMS 进程，则需要 /UNITS 命令来确保 ANSYS 和 ADAMS 之间的数据正确传输。您可以选择预定义的单位系统标签（Label = SI, CGS 等），也可以选择用户定义的系统选项（Label = USER）并输入适当的转换因子（LENFACT、MASSFACT、TIMEFACT 和 FORCEFACT）。转换系数将写入 ADAMS 输入文档 Jobname.MNF，以便正确生成负载。有关详细信息，请参阅《子结构分析指南》中的导出到 ADAMS。

All differences between the base solution units used by the ANSYS and CFX solvers will be noted in the ANSYS output file. Unit conversions are automatically applied to all loads transferred unless Label = USER. Unit conversions are not applied to any of the loads transferred between the ANSYS and CFX solvers if they use a user-defined unit system.\
ANSYS 和 CFX 求解器使用的基本求解单元之间的所有差异都将在 ANSYS 输出文档中注明。单位换算将自动应用于所有传递的荷载，除非 Label = USER。如果 ANSYS 和 CFX 求解器使用用户定义的单位系统，则单位转换不会应用于 ANSYS 和 CFX 求解器之间传递的任何载荷。

This command is valid in any processor.

```