# Installing an environment for all users

We prefer to use conda enviroments for acquisition and general PYME app use. This allows adding experimental configs without harming the current working setup etc.

Installing environments accessible for all users with miniconda (or Anaconda in general) needs a little extra work. Windows file permissions get into it as well...

## Additional packages for an acquisition system

A number of extra modules are required for an acquisition system to talk to hardware modules.

1. `pyserial` - serial communication to lasers, filterwheels etc. Installation: `conda install pyserial`
2. `pywin32` - this one is required for the interface to the Nikon Ti. This may be already installed with `pyme-depends`, i.e. part of the basic PYME install on windows. Update: this seems already installed with `pyme-depends`
3. `pywinusb` - this one is required if you want to use a spacenav device; currently best installed with `pip` it seems...

As a quick summary a terse sequence of commands that achieves a suitable install:

```DOS
# conda config --append channels anaconda # this should not be required
conda config --add channels david_baddeley
conda create -p c:\python-support-files\envs\pyme-shared python=3.7 pyme-depends

REM probably best set via System Environment Variables settings
set CONDA_ENVS_PATH=c:\python-support-files\envs
REM install a couple of packages manually
conda activate pyme-shared
conda install statsmodels # for PYME-extra
conda install pyserial # for PYMEAcquire serial devices
pip install pywinusb # required for spacenav

REM after cloning the relevant repos go into respective directories and build
cd \python-support-files
cd pyme-py37
python setup.py develop
REM a quick minimal test everything sort of works
dh5view -t -m lite

REM same for PYME-extra
cd ..\PYME-extra
python setup.py develop
python install_plugins.py dist

REM if you are using PYMEnf install as well
REM extract pymenf.zip
cd ..\pymenf
python setup.py develop
python install_plugins.py dist
```

## Create the environment

Install a fresh environment by prefix into a generally accessible directory - in these examples we call our environment `pyme-shared`

```DOS
conda config --append channels anaconda
conda config --add channels david_baddeley
conda create -p c:\python-support-files\envs\pyme-shared python=3.7 pyme-depends

```

**Note**: The `pyserial` package needed to be installed separately since it is needed by a number of backends and apparently not automatically provided with the `pyme-depends` metapackage. Done easily via:

	conda install pyserial

## Make more easily usable for all users

Add the parent directory of those environments to the `CONDA_ENVS_PATH` environment variable.

Example:

	set CONDA_ENVS_PATH=C:\python-support-files\envs


With that setting (probably best set as system environment variable so that every user has this automatically available) individual users can see this environment in their list of environments:

	conda env list

and also activate this environment using the usual

	conda activate pyme-shared

## Building and installing the various PYME packages

Detailed instructions for building and installing git tools, C compiler etc see our separate notes on how to [install PYME for Win 10](../Installing-PYME-with-py3-win10.md).

### PYME-cs-siteconfig

In addition we need the repository that has our site configuration details on these acquisition PCs. [PYME-cs-siteconfig](https://github.com/csoeller/PYME-cs-siteconfig) has init files, launchers and custom protocols, amongst other things. Consult the [PYME-cs-siteconfig installer page](PYME-cs-siteconfig.md) for more details.

## Setting up pixel sizes for cameras

With the new install the pixel sizes for all typically used cameras need to be set anew. This can occur from the `Camera>Set Pixel Size` menu in a suitable `pymeacquire` run that uses the camera in question. Numbers from the current settings could be looked up from the earlier install or use a calibration slide to use the opportunity and check the calibration for good.

## Making the install accessible for standard users

### Check that users can find the relevant executables

This may require adding to the `PATH` in a `CMD` window and using the windows `where` command to locate executables and see where they are found. Note that we will later typically set the `PATH` variable appropriately in the launcher scripts that standard users will run. See below on launchers.

### Directory permissions

We needed to set permissions for the files in the environment. Eventually, I tried to set `Full Control` for the `envs` directory and also tick the box `Replace all child object permissions...`. This was eventually done for both the `Users` and `Authenticated Users` groups.

This seems to have done the job but a number of questions remain:

- is setting this for both groups necessary?
- do we need this done via the `Advanced Settings` tab and tick the `Replace all child...` box?

#### Update

On the Dell we checked this again. Apparently, `Authenticated Users` is the group to use and we also had to do this for both `C:\ProgramData\Miniconda3` and `C:\python-support-files`, giving them full control and enable child object permission inheritance. This seemed important so that a normal user can use `conda` and the environments we created.


### Tests

To test permissions, login as a standard user, activate the environment in question (for us typically `pyme-shared`) and try to execute `python.exe` from an Anaconda shell, e.g.

	python -V

If this prints the Python version all is fine. If you get `permission denied` further permission fiddling is required.

Below we show the settings of the `envs` folder and the permissions on `python.exe`

![](images/file-permissions-envs.png)

![](images/file-permissions-python.png)

## Launchers

Launchers are created to simplify app opening and are supposed to take care of environment variables, conda virtualenv (virtual environment) activation and any other setup aspects that are best hidden from the average user. See also the [launcher page](../PYME-windows-launchers.md).

### Put launchers on everybody's desktop

The launchers are typically in a site specific directory. Create shortcuts for all relevant launchers in that directory (typically as admin) and then move these shortcuts into the public desktop. The following instructions detail how to go about that (source [superuser.com](https://superuser.com/questions/984866/how-to-make-a-desktop-shortcut-available-for-all-users-in-windows-10)):

Put it in this folder (exactly like below, with the % characters):

	%public%\Desktop

e.g. using this command:

	copy file.lnk %public%\Desktop

This should be more reliable in case Users location is changed.

Bonus: other ways to open the public desktop in Explorer:

- you can paste `%public%\Desktop` in the Explorer location bar
- or hit `Win+R` and enter `%public%\Desktop`


## Tests

The main tests include

 - test that PYME works in principle (e.g. using `dh5view` test commands, see above); probably also want to open an `.h5r` file - here cloning our [example data repo](https://github.com/csoeller/PYME-extra-sample-data) is a good starting point
 - verify that standard users can access and run PYME, see above for some tests, e.g. making sure they can execute the Python interpreter 