# set_log_level

````{method} Mapdl.set_log_level(loglevel)

Sets log level

Parameters:
-----------

  loglevel : *`str`* , *`int`*
  : Log level. Must be one of: `'DEBUG'`, `'INFO'`, `'WARNING'`, `'ERROR'`.

Examples
---------

Set the log level to debug

```python
>>> mapdl.set_log_level('DEBUG')
```

Set the log level to info

```python
>>> mapdl.set_log_level('INFO')
```

Set the log level to warning

```python
>>> mapdl.set_log_level('WARNING')
```

Set the log level to error

```python
>>> mapdl.set_log_level('ERROR')
```

````