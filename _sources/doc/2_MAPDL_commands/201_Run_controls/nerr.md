# nerr

```{py:method} Mapdl.nerr(nmerr='', nmabt='', abort='', ifkey='', num='', **kwargs)

Limits the number of warning and error messages displayed.\
限制显示的警告和错误信息的数量。

APDL Command: /NERR

Parameters:
-------------

  *nmerr*
  : Maximum number of warning and error messages displayed per command. Defaults to 5 for interactive runs with the GUI turned on, 20 for interactive runs with the GUI turned off, 200 for batch runs. If NMERR is negative, the absolute value of NMERR is used as the maximum number of warning and error messages written to the error file (file.ERR) per command, as well as the maximum number of messages displayed per command.\
  每条命令显示的警告和错误信息的最大数量。对于打开 GUI 的交互式运行，默认为 5，对于关闭 GUI 的交互式运行，默认为 20，对于批处理运行，默认为 200。如果 NMERR 为负值，NMERR 的绝对值将作为每个命令写入错误文件（file.ERR）的最大警告和错误信息数量，以及每个命令显示的最大信息数量。

  *nmabt*
  : Maximum number of warning and error messages allowed per command before run aborts (must be greater than zero). Maximum value is 99,999,999. Defaults to 10,000.\
  在运行中止前，每个命令允许的最大警告和错误信息数量（必须大于零）。最大值为 99,999,999。默认为 10,000。

  *abort*
  : Abort level key. Set to 0 for default abort behavior, -1 to never abort, and -2 to abort after nmabt errors. Altering the abort level key is not recommended, but can be helpful for avoiding an abort within /BATCH mode but using pyansys interactively.\
  终止级别键。设置为 0 表示默认中止行为，-1 表示从不中止，-2 表示在 `nmabt` 错误后中止。不建议改变中止级别键，但对于在 */BATCH* 模式下避免中止，但以交互方式使用 `pyansys`，可能会有帮助。

  *ifkey*
  : Specifies whether or not to abort if an error occurs during a /INPUT operation:\
  指定在 /INPUT 操作过程中发生 error 时是否要终止操作：\
  0 or OFF - Do not abort. This option is the default.\
  1 or ON - Abort.

  *num*
  : The number of invalid command warnings before a stop warning will be issued:\
  在发出停止警告之前，无效命令警告的数量：\
  0 - Disables the stop warning/error function. 禁用停止warning/error功能。\
  n - An integer value representing the number of warnings that will be encountered
before prompting the user to stop (default = 5). The first error encountered will ALWAYS result in a prompt. 一个整数，代表在提示用户停止之前所遇到的警告数量（默认=5）。遇到的第一个错误总是会导致提示。

Notes
-------

Limits the number of warning and error messages displayed for any one command in an interactive run.\
限制交互式运行中任何一条命令所显示的警告和错误信息的数量。

Warning and error messages continue to be written to Jobname.ERR regardless of these limits (unless NMERR is negative).\
无论这些限制如何，警告和错误信息将继续写入 Jobname.ERR 文件中（除非 *NMERR* 为负值）。

Issue this command with NUM = n to specify the number of “invalid command” warnings to be encountered before the user is prompted to stop. You can then continue or abort the run. If you choose to abort the run, the log file can be saved so that any of the processing up to that point can be appended to an input that rectifies the condition. A batch run always aborts on the first error. Issue /NERR,STAT to list current settings.\
发出这条命令时，*NUM=n* 可以指定在提示用户停止之前遇到的 "无效命令" 警告的数量。然后你可以继续或中止运行。如果你选择中止运行，可以保存日志文件，这样到那时的任何处理都可以附加到纠正条件的输入上。批量运行总是在第一个错误时中止。发出 `/NERR,STAT` 以列出当前设置。

Issue /NERR,DEFA to reset values to initial defaults.\
发布 `/NERR,DEFA`，将数值重置为初始默认值。

An IFKEY value of 1 or ON causes the ANSYS program to abort immediately upon encountering an error during a file /INPUT operation. However, use of this option may cause the following conditions to occur:\
*IFKEY* 值为 1或 ON 会使 ANSYS 程序在文件 /INPUT 操作中遇到错误时立即中止。然而，使用这个选项可能会导致以下情况的发生：

- The /INPUT command may abort if issued for a log file (jobname.log).\
如果对一个日志文件（jobname.log）发出 /INPUT 命令，可能会中止。

- Some macros may abort.\ 某些宏可能会中止。

- A CAD connection may fail after reading only a small portion of a CAD model.\
一个 CAD 连接可能在只读取了一个 CAD 模型的一小部分后就失效了。

The command is valid in any processor.\
该命令在任何处理器中都有效。



```