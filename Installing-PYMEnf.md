# Install PYMEnf (PYME-nonfree)

## Unzip the pymenf code

I have resorted to distributing the PYMEnf code via a zip archive (long story why this is not shared via github at the moment). The file ```pymenf.zip``` is available from our ```CS lab``` Teams group chat in the ```Files``` section.

Get the archive from there and unpack into the same directory that has already the ```python-microscopy``` and ```PYME-extra``` repos in it. Unpacking it should create a new folder ```pymenf```.


## Build the pymenf code

You want to now cd into the newly created pymenf directory and build the pymenf package as shown below.

        # make sure you are in a terminal where the enviroment is activated!!!!
        #
        # normally you activate the environment first using the conda command below
        # omit this step if you are already in the environment in the command shell
        conda activate pyme-default-plain
        # cd to the PYMEnf subdirectory before issuing the commands below!
        
        python setup.py develop
        python install_plugins.py

Note that we leave out the ```dist``` argument in the plugin install call since we are installing to your local login. We could probably also install to dist, but I want to try it like this first.

## Check that we can use pymenf functionality in visgui

If the build and plugin install worked ok, we should now have a new functionality for drift correction within VisGUI. In the ```Corrections``` menu there should be a new choice ```Model based drift correction``` as shown below. Check if this is present and if not it is time to start the trouble shooting:

![pymenf-menu](images/pymenf-corrections.png)


```python

```
