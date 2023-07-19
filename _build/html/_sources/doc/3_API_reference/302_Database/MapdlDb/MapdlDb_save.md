# save

````{py:method} MapdlDb.save(fname, option='ALL')

Save the MAPDL database to disk.

Parameters:
----------

  *fname*: `str`
  : Filename to save the database to.

  *option*: `str`
  : The mode for saving the database, either:
  - “ALL” - Both the model and the solution
  - “MODEL” - Just the model
  - “SOLU” - Just the solution


Examples
-------

```py

>>> mapdl.db.save('model.db',option=)

````







```