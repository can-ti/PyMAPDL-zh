# time

````{property} property PostProcessing.time: float

Time associated with current result in the database.

Examples
--------

Time of the current result of a modal analysis

```python
>>> mapdl.post1()
>>> mapdl.set(1, 1)
>>> mapdl.post_processing.time
1.0

```



````