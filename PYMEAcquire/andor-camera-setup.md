# Andor camera setup

## Install relevant SDK

You generally need the Andor SDKs to enable camera support. We typically also buy the Andor Solis software so that we have a positive control that certain camera aspects are supported, work as expected etc.

We now run our acquisition systems under Windows 10.

## Initial testing

If you have access to Solis with your camera, it is always a good idea to talk to it via Solis first and make sure it is found and working ok with that software interface. Presumably there are other free ways, e.g. using micromanager etc.

## Make SDK DLLs detectable

- Add the SDK DLL location(s) to `PATH`; this is important so that DLLs are found when loading our backends that need access to these DLLs
- either add locations to system `PATH` or it maybe better achieved via launcher scripts

The simplest way to ensure proper detection of required DLLs at startup seems to be to add the directories these are in to the `PATH` environment variable.

This can be done via editing the system `PATH` variable, for example using the GUI to edit system (and user level) environment variables under windows.

A possible preferable way is to use the concept of launcher scripts that set the environment as needed, activate the desired conda environment and any other setup work that is useful for the specific application being launched.

### Example launcher

We have an example launcher script [pymeacquire-zyla-py37.bat](https://github.com/csoeller/PYME-exeter-siteconfig/blob/master/launchers/Bern-PC184/pymeacquire-zyla-py37.bat) in our [site-config repo](https://github.com/csoeller/PYME-exeter-siteconfig).

## Add camera configurations if needed

Latest PYME has the ability to add camera noise properties to the camera folder in one of the configuration subdirectories. This is described in the `PYME.Acquire.Hardware.camera_noise` docs and easiest inspected (while making sure to be in the right conda environment) using `pydoc`, e.g.:

	pydoc PYME.Acquire.Hardware.camera_noise

There are examples of `.yaml` files for typical cameras that we use.

## Tests

Now it is probably best to run the camera with a generic config file for the camera model you are using. As an example, here is a link to a config script [init_Zyla_n.py](https://github.com/csoeller/PYME-exeter-siteconfig/blob/master/init_scripts/generic/init_Zyla_n.py) for a Zyla, the launcher linked above uses it.