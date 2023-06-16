# unpause

```{py:method} Mapdl.unpause(**kwargs)

Restores use of a temporarily released product license.\
恢复使用一个临时释放的产品许可证。

APDL Command: UNPAUSE

Notes
-------

The UNPAUSE command restores use of a temporarily released (paused) product license. The command is valid only after a previously issued PAUSE command.\
UNPAUSE 命令恢复对临时释放（暂停）的产品许可证的使用。该命令只有在先前发出 PAUSE 命令后才有效。

When use of the product license is paused via the PAUSE command, no other operation (other than SAVE or /EXIT) is possible until you issue the UNPAUSE command.\
当通过 PAUSE 命令暂停使用产品许可证时，在你发出 UNPAUSE 命令之前，不可以有其他操作（除 SAVE 或 /EXIT 外）。

For more information, see the documentation for the PAUSE command and the *ANSYS,Inc.Licensing Guide*.\

```