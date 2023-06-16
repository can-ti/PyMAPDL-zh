# resume

```{py:method} Mapdl.resume(fname='', ext='', nopar='', knoplot='', **kwargs)

Resumes the database from the database file.\
从数据库文件中恢复数据库。

APDL Command: `RESUME`

Parameters:
-----------

  *fname*
  : File name and directory path (248 characters maximum, including the characters needed for the directory path). An unspecified directory path defaults to the working directory; in this case, you can use all 248 characters for the file name.

  *ext*
  : Filename extension (eight-character maximum).

  *nopar*
  : Parameter resume key:\
  **0** - All data in the database, including the scalar parameters, are replaced with the data saved on File.DB (default).\
    数据库中的所有数据，包括标量参数，都被保存在 File.DB 上的数据取代（默认）。\
  **1** - All data in the database, except the scalar parameters, are replaced with the data saved on File.DB.\
    数据库中的所有数据，除了标量参数，都被保存在 File.DB 上的数据所取代。

  *knoplot*
  : If equal to 1, will suppress automatic plot. Otherwise, if the GUI is on and this `RESUME` command was not read from a file, the selected elements from Fname are plotted. (If there are no selected elements, selected nodes are plotted. If no nodes, volumes; if no volumes, areas; if no areas, lines; if no lines, keypoints. If there are no selected keypoints, the screen is erased.)\
  如果等于 1，将抑制自动绘图。否则，如果 GUI 是打开的，并且这个 `RESUME` 命令不是从文件中读取的，那么 *Fname* 中的选定元素将被绘制出来。（如果没有选定的单元，则绘制选定的节点；如果没有节点，则绘制；如果没有体，则绘制面；如果没有面，则绘制线条；如果没有线条，则绘制关键点。如果没有选定的关键点，屏幕就会被擦除）。

Notes
-----

The `RESUME` command resumes a database file into the ANSYS program. The command causes the database file (File.DB) to be read, thereby resetting the database (including any geometry settings) either a) as it was at the last `SAVE` command, or b) as it was saved with the last `/EXIT` command, whichever was last.\
`RESUME` 命令将数据库文档恢复到 ANSYS 进程中。该命令会读取数据库文档（File.DB），从而重置数据库（包括任何几何设置）：a） 与上次 `SAVE` 命令时相同，或 b） 使用最后一个 `/EXIT` 命令保存时，以最后一个命令为准。

For multiple load step analyses (because only the data for one load step at a time may reside in the database), the load step data restored to the database will correspond to the load step data written when the save occurred.\
对于多个荷载步的分析（因为每次只有一个荷载步的数据可能存在于数据库中），恢复到数据库中的荷载步数据将与保存发生时写入的荷载步数据一致。


If the database file was saved in another ANSYS, Inc. product, it may contain element type and KEYOPT specifications which are invalid in the resuming product. Immediately after the database resume is completed, you should redefine these invalid element types and KEYOPT settings to valid ones (`ET, KEYOPT`).\
如果数据库文件保存在另一个 ANSYS，Inc. 产品中，它可能包含单元类型和 KEYOPT 选项，这些在 resume 中是无效的。在数据库恢复完成之后，应该立即将这些无效的单元类型和 KEYOPT 设置重新定义为有效的单元类型 (`ET,KEYOPT`)。

The `NOPAR = 1` option should not be used if array parameters are defined, as existing array parameters might be redefined with arbitrary values. For a more general method of preventing the replacement of both scalar and array parameters, see `PARSAV` and `PARRES`.\
如果定义了数组参数，则不应使用 `NOPAR = 1` 选项，因为可以使用任意值重新定义现有数组参数。有关防止替换标量和数组参数的更通用方法，请参阅 `PARSAV` 和 `PARRES`。

If a radiosity mapping data file (.RSM file) was saved by the previous SAVE command, that mapping file must be present in the directory along with the database file in order for radiosity surface elements (SURF251, SURF252) to be correctly mapped onto the model when RESUME is issued.

This command is valid in any processor. If used in the solution processor, this command is valid only within the first load step.

```