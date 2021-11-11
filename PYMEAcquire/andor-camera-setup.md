# Andor camera setup

## Install relevant SDK

You generally need the Andor SDKs to enable camera support. We typically also buy the Andor Solis software so that we have a positive control that certain camera aspects are supported, work as expected etc.

We now run our acqusition systems under Windows 10.

## Make SDK DLLs detectable

- Add SDK DLL location(s) to `PATH`; important so that DLLs are detected when loading
- either add to system `PATH` or maybe better achieved via launcher script

The simplest way to ensure proper detection of required DLLs at startup seems to be to add the directories these are in to the `PATH` environment variable.

This can be done via editing the system `PATH` variable, for example using the GUI to edit system (and user level) environment variablkes under windows.

A possible preferrable way is to use the concept of launcher scripts that set the environment as needed, activate the desired conda environment and any other setup work that is useful for the specific application being launched.

**TODO**: add launcher links

## Add camera configurations if needed

Latest PYME has the ability to add camera noise properties to the camera folder in one of the configuraton subdirectories. This is described in the `PYME.Acquire.Hardware.camera_noise` docs and easiest inspected (while making sure to be in the right conda environment) using `pydoc`, e.g.:

	pydoc PYME.Acquire.Hardware.camera_noise

There are examples of `.yaml` files for typical cameras that we use.

## Tests

**TODO**: add some tests to verify correct install