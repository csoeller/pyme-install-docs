# pyme-install-docs

Here we provide some fairly detailed docs how to install a working python-microscopy setup on windows 10 machines. All packages are installed in ```develop``` mode so that it is quite easy to pull in updates from github without having to do any rebuilds. Note that most of the setup instructions are platform independent though. This has been geared to allow my group to install the latest python-microscopy and pyme-extra on their home machine now that we operate in lockdown.

We describe here a python 2 based development install as it is still easier to manage on windows due to the compiler requirements. On other platforms a python 3 based development install should work fairly well now, I am about to give it a spin on macos.

It also reflects the move of all key repositories to github since bitbucket in its infinite wisdom decided to discontinue mercurial repositories. The docs curated here are to be read in addition to the authorative installation instructions at [python-microscopy.org](http://www.python-microscopy.org/). Our docs try to hold the user a little more by the hand assuming hopefully not too much coding experience on the side of the reader.

Some instructions could be a little specific to the local users at U Exeter but I should imagine that others can use these instructions and I welcome feedback about issues encountered by others.

The docs are in the form of jupyter notebooks that mostly have markdown cells. I could have done the whole thing in markdown files to start with but the cell based structure of notebooks seemed appealing as does the fact that I can intersperse working python code if/when needed. Finally, github renders these notebooks just fine.

Thanks go as usual to David Baddeley and other core contributers to PYME (we also dabble in contribs and make the pyme-extra repo available for experimental functionality that extends PYME). PYME is IMHO the standout most powerful SMLM package on the planet right now but with power comes complexity - think about the skills required to properly operate a milling machine or a lathe in a mechanical workshop, that kind of thing.

CS (while in #lockdown)
