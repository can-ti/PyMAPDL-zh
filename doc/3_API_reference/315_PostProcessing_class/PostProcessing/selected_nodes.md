# selected_nodes

````{property} property PostProcessing.selected_nodes: ndarray

Mask of the selected nodes.

Examples
----------

```python
>>> mapdl.post_processing.selected_nodes
array([False, False, False, ..., True, True, True])
```

If you want the element numbers of the selected nodes.

```python
>>> mapdl.post_processing.selected_nodes.nonzero()[0] + 1
array([1, 2, 3, 4, 5, 6, 7, 8, 9])
```


````