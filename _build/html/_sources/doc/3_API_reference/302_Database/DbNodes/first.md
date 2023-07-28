# first

````{method} DbNodes.first(inod=0)

Return the number of the first node.

This starts at `inod`, defaults to the first node in the model.\
从 inod 开始，默认为模型中的第一个节点。


Parameters:
-----------

  *inod* : *`int`*,*`optional`*
  : The first node number to consider as the “first node”.

Returns:
---------

  *`int`*
  : The first node number within either selected or all nodes.

Examples
--------

Return the first selected node.

```python
>>> nodes.first()
1
```

Return the first node after node 10.

```python
>>> nodes.first(inod=10)
11
```



````