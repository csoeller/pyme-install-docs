# Installing an environment for all users

We prefer to use conda enviroments for acquisition and general PYME app use. This allows adding experimental configs without harming the current working setup etc.

Installing environments accessible for all users with miniconda (or Anaconda in general) needs a little extra work. Windows file permissions will likely get into it as well...

**TODO**: notes below need fleshing out...

## Create the environment

- install by prefix in a generally accessible directory - in these examples we call our environment `pyme-shared`

## Make more easily usable for all users

- add the parent directory of those environments to the following environment variable: `CONDA_ENVS_PATH`

Example:

	set CONDA_ENVS_PATH=C:\python-support-files\envs


With that setting (probably best set as system environment variable so that every user has this automatically available) individual users can see this environment in their list of environments:

	conda env list

and also activate this environment using the usual

	conda activate pyme-shared

## Directory permissions

**TODO**: add relevant findings

## Launchers

**TODO**: add launcher info

## Tests

**TODO**: add some tests to verify correct install