# PYME win 10 app launchers in an anaconda environment

## Make batch files that set the environment and act as launchers

The examples below all use a virtualenv called `pyme-default-plain`. If an another environment is used, e.g. `pyme-py37` or `pyme-py3` etc, just replace the environment name as suitable in the examples below.

Example: file ```visgui-launcher.bat```

    @echo off
    setlocal
    rem we need to check if we need a path setting and what path is correct for conda
    set PATH=C:\ProgramData\Anaconda2\condabin;%PATH%
    
    CALL conda.bat activate pyme-default-plain
    rem echo %path%
    visgui %1
    CALL conda.bat deactivate

This can be used with the windows ```Open with...``` dialogue when you have selected a file in the file manager and ensures the proper environment is set up. First time around you need to chose ```Choose the default program``` and be sure to tick/untick the box ```Always use the selected program to open this kind of file```, depending if you want to open **all files with this extension always** with this wrapper, **or not**. Then select the batch file (e.g. ```visgui-launcher.bat```) to open the file with.

### Where to store the launchers

The launcher files are best kept in a separate folder, e.g. a ```launchers``` subfolder of the folder where the other PYME repositories are. For example, we maintain a number of machine specific launchers in the [launchers subfolder](https://github.com/csoeller/PYME-exeter-siteconfig/tree/master/launchers) of our [PYME site config repo](https://github.com/csoeller/PYME-exeter-siteconfig).

### Making desktop shortcuts to the launchers

It is also useful to make shortcuts to the launchers that appear on your desktop. Let me know if you are unsure how to do that.

### A special issue with launchworkers

The launchworkers launcher needs special attention since it creates logfiles when started. So one needs to cd to a suitable user writable directory before starting the actual launchworkers script. This has tripped me up a few times as the launching of server and workers fails siletly and it looks like zeroconf can't connect.

This has led me to look for a zeroconf issue when really zeroconf couldn't contact anything because server and worker processes had failed to start because they could not open their log files!!!

Here is what we do at the moment:

    @echo off
    setlocal
    set PATH=C:\ProgramData\Anaconda2\condabin;%PATH%
    
    cd C:\python-support\log
    
    CALL conda.bat activate pyme-default-plain
    rem echo %path%
    launchworkers
    CALL conda.bat deactivate

I am not sure that ```C:\python-support\log``` is the best choice for a single user, you may just make a sub-directory called ```log``` within your user directory tree that holds the other PYME repositories. Whichever directory is chosen, make sure that it is user writable in terms of permissions.
