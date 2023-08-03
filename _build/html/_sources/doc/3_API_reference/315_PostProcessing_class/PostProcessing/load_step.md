# load_step

````{property} property PostProcessing.load_step: int

Current load step number

Examples
--------

Get all the time values after loading POST1.

```python
>>> mapdl.post1()
>>> mapdl.set(2, 2)
>>> mapdl.post_processing.load_step
2
```

````