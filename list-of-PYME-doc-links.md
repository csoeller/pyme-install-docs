# Overview of various PYME docs, tips and tricks

This document should serve as a collection of links to more detailed documentation, tips or tricks how to use the [*Python Microscopy Environment*](https://python-microscopy.org/) or `PYME` for short.

This is still in some early alpha phase and contains various place holders etc. If you have useful feedback please let us know in [this repo's issue tracker](https://github.com/csoeller/pyme-install-docs/issues).


## Where to find general docs

- link to the [latest PYME documentation](https://python-microscopy.org/doc)
- the main [PYME website](https://python-microscopy.org/)

### Installation info

- [installation instructions](http://python-microscopy.org/doc/Installation/Installation.html) at [python-microscopy.org](http://python-microscopy.org)
- this repository: [pyme-install-docs](https://github.com/csoeller/pyme-install-docs)
- other links

## Random list of useful bits and links

### How to quickly analyse the quality of a sequence from h5 and h5r files

This should link to a future quick overview of how this can be done.

### Info on plugins

- template repository that shows how to make plugin repositories: [pyme-plugin](https://github.com/python-microscopy/pyme-plugin)
- more stuff?

### PYME launchers for windows

We like the concept of launchers for windows PYME installs. This allows you to have various Python (or more specifically [conda](https://docs.conda.io/en/latest/)) [virtualenvs](https://towardsdatascience.com/getting-started-with-python-environments-using-conda-32e9f2779307) and fire up PYME apps in these environments seamlessly.

The general concept is described in the [PYME windows launchers](https://github.com/csoeller/pyme-install-docs/blob/master/PYME%20windows%20launchers.md) document.

Some examples can be found in the [launchers subfolder](https://github.com/csoeller/PYME-exeter-siteconfig/tree/master/launchers) of our [site-config repository](https://github.com/csoeller/PYME-exeter-siteconfig).

### PYME - Saving and loading visgui recipes

A basic overview how to save and load data processing pipelines in PYME.

Video Link (via Panopto, accessible only for UoE staff): [PYME - Saving and loading visgui recipes](https://recapexeter.cloud.panopto.eu/Panopto/Pages/Viewer.aspx?id=9822295e-9e1a-48ce-a2a6-aba4008f6b34)

### PYME - finding and selecting fiducials

A basic overview how to find (locate) and then select fiducial information in PYME. This is describing the approach via [PYME-extra](https://github.com/csoeller/PYME-extra) which implements a version where we select a single fiducial and does not suffer from the problem we see using the general PYME fiducial module approach which in our hands leads to broken segments. This really needs a discussion between David and us to solve this issue properly at some stage!

The downside of our single fiducial approach is that we cannot easily take advantage of averaging.

Video Link (via Panopto, accessible only for UoE staff): [PYME - finding and selecting fiducials](https://recapexeter.cloud.panopto.eu/Panopto/Pages/Viewer.aspx?id=64c89833-784b-4556-88b4-aba400a12e91)


### PYME - applying fiducials for drift correction

A basic overview how to apply fiducial information to drift correct a data series in PYME.

Video Link (via Panopto, accessible only for UoE staff): [PYME - applying fiducials for drift correction](https://recapexeter.cloud.panopto.eu/Panopto/Pages/Viewer.aspx?id=6c516348-95da-41da-b14f-aba400a848f7)

