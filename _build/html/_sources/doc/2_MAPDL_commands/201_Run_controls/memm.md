# memm

```{py:method} Mapdl.memm(lab='', kywrd='', **kwargs)

Allows the current session to keep allocated memory.\
允许当前会话保持分配的内存。

APDL Command: MEMM

Parameters:
---------------

  *lab*
  : When Lab = KEEP, the memory manager’s ability to acquire and keep memory is controlled by Kywrd\
  当 Lab = KEEP 时，内存管理器获取和保留内存的能力由 Kywrd 控制。

  *kywrd*
  : Turns the memory “keep” mode on or off\
  ON - Keep any memory allocated during the analysis.\
  OFF - Use memory dynamically and free it up to other users after use (default).

Notes
--------------

You can use the MEMM command to ensure that memory intensive operations will always have the same memory available when the operations occur intermittently. Normally, if a large amount of memory is allocated for a specific operation, it will be returned to the system once the operation is finished. This option always maintains the highest level used during the analysis until the analysis is finished.\
你可以使用 MEMM 命令来确保在操作间歇性发生时，内存密集型操作将始终有相同的内存可用。通常情况下，如果为一个特定的操作分配了大量的内存，一旦操作结束，这些内存就会被退回到系统中。这个选项总是保持分析过程中使用的最高级别，直到分析结束。

The MEMM command does not affect the value you specify with the -m switch. When you allocate memory with the -m switch, that amount will always be available. However, if dynamic memory allocation in excess of the -m value occurs, you can use the MEMM command to ensure that amount is retained until the end of your analysis.\
MEMM 命令并不影响你用 -m 开关指定的数值。当你用 -m 开关分配内存的时候，这个数量将永远是可用的。然而，如果发生了超过 m 值的动态内存分配，你可以使用 MEMM 命令来确保这个量被保留到你的分析结束。

```