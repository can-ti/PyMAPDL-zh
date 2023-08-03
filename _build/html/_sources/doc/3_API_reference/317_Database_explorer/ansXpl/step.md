# step

````{method} ansXpl.step(where)

Go down in the tree of records

Parameters:
-----------

  where : *`str`*
  : Path to follow. This path can be composed of several levels, for example `"BRANCH1::SUBBRANCH2::.."`.\
  要跟踪的路径。该路径可以由多个层级组成，例如`"BRANCH1::SUBBRANCH2::..."`。

Returns:
-------
  `str`
  : Response from MAPDL.

Examples
-------

```python
>>> xpl.step('MASS')
>>> print(xpl.where())
 =====      ANSYS File Xplorer : Display Current Location
 Current Location : FULL::MASS
    File Location : 7644
```



````