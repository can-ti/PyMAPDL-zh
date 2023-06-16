# quit

```{py:method} Mapdl.quit(**kwargs)

Exits a processor.

APDL Command: `/QUIT`

Notes
------

This is an alternative to the FINISH command. If any cleanup or file writing is normally done by the FINISH command, it is bypassed if the /QUIT command is used instead. A new processor may be entered after this command. See the /EXIT command to terminate the run.\
这是对 FINISH 命令的一种替代。如果任何清理或文件写入通常由 FINISH 命令完成，那么如果用 /QUIT 命令代替，就会绕过它。在这个命令之后可以进入一个新的处理器。参见 /EXIT 命令以终止运行。


This command is valid in any processor. This command is not valid at the Begin level.

```