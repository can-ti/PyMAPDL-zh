# next

````{py:method} DbNodes.next()

Return the number of the next selected node.

You must first call `DbNodes.first()`.

Returns:
---------

  `int`
  : The next selected node number. Returns 0 if there are no more nodes.\
  下一个选中的节点编号。如果没有更多节点，则返回 0。

Examples
-----------

Call `DbNodes.first()` first.

```python

>>> nodes.first()
1

```

Then get the next node.

```python

>>> elems.next()
2

```

````