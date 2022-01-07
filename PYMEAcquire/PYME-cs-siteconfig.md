# Installing PYME-cs-siteconfig on acquisition PCs

The [PYME-cs-siteconfig](https://github.com/csoeller/PYME-cs-siteconfig) repository is required on our production machines to get access to the local configuration files (init files) and has a set of launchers, potential custom protocols and also some splitter config in the form of dye ratios with the various splitter dichroics.

## Clone the repo

Clone the repo using the usual approaches.

## Install custom protocols

This is done using

    python install_plugins.py dist

## Init files

We generally pick these up via the [launcher scripts](../PYME-windows-launchers.md) which include a path to the init file location.

## Dye Ratios

The repo also contains a file with dye ratios for a number of splitter dichroics.

**TODO**: need to remind myself how dyeratio JSON file gets picked up by PYME!
