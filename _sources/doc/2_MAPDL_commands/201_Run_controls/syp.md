# syp

```{py:method} Mapdl.syp(string='', arg1='', arg2='', arg3='', arg4='', arg5='', arg6='', arg7='', arg8='', **kwargs)

Passes a command string and arguments to the operating system.\
将一个命令字符串和参数传递给操作系统。

APDL Command: `/SYP`

Parameters:
------------

  *string*
  : Command string (cannot include commas). See also the `/SYS` command.\
  命令字符串（不能包括逗号）。也请参见 `/SYS` 命令。

  *arg1, arg2, arg3, … , arg8*
  : Arguments to be appended to the command string, separated by blanks, commas, or other delimiter characters (see the *Operations Guide*). The arguments may be numbers, parameters, or parametric expressions.\
  要追加到命令字符串中的参数，用空格、逗号或其他分隔符分隔（见 *Operations Guide*）。参数可以是数字、参数或参数化表达式。

Notes
-------

Passes a command string to the operating system for execution, along with arguments to be appended to the command string. See the *Operations Guide* for details. ANSYS may not be aware of your specific user environment. For example, on Linux this command may not recognize aliases, depending on the hardware platform and user environment.\
传递一个命令字符串给操作系统执行，以及附加在命令字符串上的参数。详情见 *Operations Guide*。ANSYS 可能不知道你的具体用户环境。例如，在 Linux 上这个命令可能无法识别别名，这取决于硬件平台和用户环境。

This command is valid in any processor.

```