# slashstatus

```{py:method} Mapdl.slashstatus(lab='', **kwargs)

Lists the status of items for the run.\
列出运行项目的状态。

APDL Command: /STATUS

Parameters:
-----------

  *lab*
  : Items to list status for:\
  ALL - List all below (default).\
  TITLE - List only titles, Jobname, and revision number.\
  UNITS - List only units.\
  MEM - List only memory data statistics.\
  DB - List only database statistics\
  CONFIG - List only configuration parameters.\
  GLOBAL - Provides a global status summary.\
  SOLU - Provides a solution status summary.\
  PROD - Provides a product summary.

Notes
-----

Displays various items active for the run (such as the ANSYS revision number, Jobname, titles, units, configuration parameters, database statistics, etc.).\
显示运行中的各种项目（如 ANSYS 修订号、Jobname、标题、单位、配置参数、数据库统计等）。

This command is valid in any processor.

```

