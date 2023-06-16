# pause

```{py:method} Mapdl.pause(**kwargs)

Temporarily releases the current product license.
暂时释放当前的产品许可证。

APDL Command: PAUSE

Notes
--------

The PAUSE command temporarily releases (or pauses) the current product license so that another application can use it.\
PAUSE 命令暂时释放（或暂停）当前的产品许可证，以便其他应用程序可以使用它。

This application consumes a license as soon as you launch it, and retains that license until it is finished. If you launch the product interactively, the license is retained until you either close the application or issue a PAUSE command via the command line.\
这个应用程序在你启动时就会消耗一个许可证，并保留该许可证直到它结束。如果你以交互方式启动该产品，许可证将被保留，直到你关闭该应用程序或通过命令行发出 PAUSE 命令。

No other operation (other than SAVE or /EXIT) is possible in the current application while use of the product license is paused.
在暂停使用产品许可证时，在当前应用程序中不可以执行有其他操作（除了 SAVE 或 /EXIT）。

When the second application has finished and releases the license, issue an UNPAUSE command via the command line to restore use of the license to the current application.
当第二个应用程序完成并释放许可证时，通过命令行发出 UNPAUSE 命令，将许可证的使用恢复到当前应用程序。

For more information, see the ANSYS,Inc.Licensing Guide.


```