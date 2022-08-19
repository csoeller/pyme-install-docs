## Instructions to install PYME natively on macos ARM64 (M1, M2 etc)

### Installing miniconda and xcode command line tools

Everything is generally done in a terminal window that runs natively.

We start with a native miniconda install:

```shell
wget https://repo.anaconda.com/miniconda/Miniconda3-latest-MacOSX-arm64.sh # as seen at https://towardsdatascience.com/how-to-install-miniconda-x86-64-apple-m1-side-by-side-on-mac-book-m1-a476936bfaf0
sh Downloads/Miniconda3-latest-MacOSX-arm64.sh  # accept all defaults for miniconda prompts
```

That installed a small base install with Python 3.9.

Then I picked up the `xcode` command-line tools which is quite easy. There are a number of ways, a very easy one is just to type a command like `clang` at the terminal prompt and then you are immediately prompted/asked if you would like to install the xcode command line tools. See also https://www.freecodecamp.org/news/install-xcode-command-line-tools/. 

### Installing PYME proper

I made an environment to build PYME in and based that on Python 3.8 as a well tested version according to David Baddeley:

```shell
conda create -n pyme38_2 python=3.8
conda activate pyme38_2
```

Next we install numpy, notably an accelerated version, whereas standard conda-forge packages seem to be not very optimised.

```shell
# install accelerated numpy
conda install -c conda-forge cython pybind11
pip install --no-binary :all: --no-use-pep517 numpy # this gives us an accelerated numpy, see also https://stackoverflow.com/questions/69848969/how-to-build-numpy-from-source-linked-to-apple-accelerate-framework
conda config --set pip_interop_enabled true # apparently needed so no new numpy is pulled in in next conda command…, see also https://stackoverflow.com/questions/70240506/why-python-native-on-m1-max-is-greatly-slower-than-python-on-old-intel-i5
```

Then we collect the other depencies, mostly from conda-forge with the exception of `wxpython` which needs a pip install. The version installed was `4.2.0` and seems to work ok.

```shell
# install other dependencies
conda install -c conda-forge scipy matplotlib pytables pyopengl jinja2 cython pip requests pyyaml psutil pandas scikit-image scikit-learn sphinx
conda install -c conda-forge traits traitsui==7.1.0 pyface==7.1.0
conda install -c conda-forge python.app
conda install -c conda-forge toposort
pip install wxpython
```

Finally, we build PYME itself, as usual using a development install.

```shell
# build PYME
cd pyme38 # this should be your directory with the latest PYME source
/Users/csoe002/miniconda3/envs/pyme38_2/python.app/Contents/MacOS/python setup.py develop
dh5view -t
```

This seems to give a working install, still testing but most things with `dh5view` and `PYMEVis` seem fine.

### Getting jupyter notebook support going

This needed another quick conda install:

```shell
conda install -c conda-forge notebook
```

I then tried opening a new python3 notebook and got an error:

```
500 : Internal Server Error
```

A quick google led me to this [stackoverflow discussion](https://stackoverflow.com/questions/36851746/jupyter-notebook-500-internal-server-error) which suggested to run

```
conda install nbconvert==5.4.1
```

Now, I am not sure that the pinned version is still the best option (the previous conda command had installed version `nbconvert-5.6.1`), but I gave it a go anyway (leaving the option to tweak to a later version once it is clear in which version the issue occurs) and did

```shell
conda install -c conda-forge nbconvert==5.4.1
```

which indeed fixed the issue and now I can open notebooks just fine.