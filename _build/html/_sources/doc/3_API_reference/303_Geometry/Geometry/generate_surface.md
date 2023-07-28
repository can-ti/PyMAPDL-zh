# generate_surface

````{method} Geometry.generate_surface(density=4, amin=None, amax=None, ninc=None)

Generate an all-triangular surface of the active surfaces.

Parameters:
---------

  *density* : *`int`* , *`optional`*
  : APDL smart sizing option. Ranges from 1 (worst) to 10 (best).

  *amin* : *`int`* , *`optional`*
  : Minimum APDL numbered area to select. See `mapdl.anum` for available areas.

  *amax* : *`int`* , *`optional`*
  : Maximum APDL numbered area to select. See mapdl.anum for available areas.

  *ninc* : *`int`* , *`optional`*
  : Steps to between amin and amax.


````