# Log of py3 related install or runtime issues

## no module dispatch

I was trying to run acquisition on a win10 PC (phy-lmx2cpu) with a py3 PYME install.
Got an error that a module named dispatch was missing.

Fixed by

	conda install dispatch

Note that I searched for dispatch first:


	conda search dispatch

which printed:

```
Loading channels: done
# Name                       Version           Build  Channel
dispatch                         1.0          py27_0  david_baddeley
dispatch                         1.0          py36_0  david_baddeley
dispatch                         1.0          py37_0  david_baddeley
```

This seems to indicate this is a module supplied by David's channel only.
