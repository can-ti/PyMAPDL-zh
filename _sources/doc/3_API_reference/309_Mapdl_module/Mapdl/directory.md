# directory

````{property} Mapdl.directory: str

Current MAPDL directory.

Examples
--------

Directory on Linux

```python
>>> mapdl.directory
'/tmp/ansys'
```

Directory on Windows

```python
>>> mapdl.directory
'C:/temp_directory/'
```

Setting the directory

```python
>>> mapdl.directory = 'C:/temp_directory/'
None
```

In case the directory does not exist or it is not accessible, cwd (_MapdlCore.cwd()) will raise a warning.


````