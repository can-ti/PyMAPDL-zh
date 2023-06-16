# sys

````{py:method} Mapdl.sys(cmd)

Pass a command string to the operating system.

APDL Command: `/SYS`

Passes a command string to the operating system for execution (see the *Operations Guide*). Typical strings are system commands such as list, copy, rename, etc. Control returns to the ANSYS program after the system procedure is completed. ANSYS may not be aware of your specific user environment. For example, on Linux this command may not recognize aliases, depending on the hardware platform and user environment.\
将一个命令字符串传递给操作系统执行（见 *Operations Guide*）。典型的字符串是系统命令，如列表、复制、重命名等。在系统程序完成后，控制权回到 ANSYS 程序中。ANSYS 可能不知道你的具体用户环境。例如，在 Linux 上这个命令可能不能识别别名，这取决于硬件平台和用户环境。

Parameters:
------------

  *cmd: *`str`**
  : Command string, up to 639 characters (including blanks, commas, etc.). The specified string is passed verbatim to the operating system, i.e., no parameter substitution is performed.\
  命令字符串，最多 639 个字符（包括空格、逗号等）。指定的字符串将逐字传递给操作系统，即不进行参数替换。

Returns:
--------

  *`str`*
  : Output from the command.

Examples:
-----------

```py
>>> mapdl.sys('ls')
```

````
