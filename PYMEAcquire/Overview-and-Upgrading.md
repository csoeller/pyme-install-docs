# Overview and Upgrading PYME for Acquisition

## A brief overview of the processes on an acquisition PC

[TODO - flesh out]

## Specific notes when upgrading

Upgrades are best performed by creating a new *upgrade environment*, i.e. by making a new conda environment and installing the newer version of PYME etc into it.

There are a few things one needs to check when implementing this approach:

1. The permisiions of newly created environments need to be carefully adjusted to allow other users to execute apps in the new environment. See also the details explained in our [conda setup notes](conda-setup.md).

2. All config files need to be installed into the newly created environment (including config.ymal, camera config files, protocols). This can be done by copying across from existing environments or, perhaps better, by running the PYME siteconfig installer as `python install_config_files.py dist`. **Make sure** you do this while the new environment is activated. Details, see also the [site config install info](PYME-cs-siteconfig.md).

3. We are using a new environment variable driven way to switch to using a new conda env, so that the same launchers can seamlessly switch over without any further file editing. The gist is that users can set an environment variable `PYMEENV` that contains the name of the new environment to use. On windows, there are various ways to set this environment variable, some are illustrated below. If this variable is not set (the default) then the conda environment named `pyme-shared` is used.

### Ways to set the PYMEENV environemnt variable

[TODO - flesh out]

1. Non-admin users:

2. admin users: