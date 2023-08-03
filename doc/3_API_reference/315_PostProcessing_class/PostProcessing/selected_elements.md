# selected_elements

````{property} property PostProcessing.selected_elements: ndarray

Mask of the selected elements.

Examples
----------

```python
>>> mapdl.post_processing.selected_elements
array([False, False, False, ..., True, True, True])
```

If you want the element numbers of the selected elements.

```python
>>> mapdl.post_processing.selected_elements.nonzero()[0] + 1
array([1, 2, 3, 4, 5, 6, 7, 8, 9])
```


````