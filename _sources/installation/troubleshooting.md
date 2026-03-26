# Troubleshooting installation issues

## Problems with installing Python

First, please test that you have successfully installed the correct
Python distribution.

Find your command line (Terminal for Mac users, Command Prompt for
Windows users) and type `python`. You should see something like this:

```
$ python
Python 3.9.13 (main, Aug 25 2022, 18:29:29) 
[Clang 12.0.0 ] :: Anaconda, Inc. on darwin
Type "help", "copyright", "credits" or "license" for more information.
```

If you get an error message, or you don’t see “Anaconda” in the initial
message, you should go to the [installing
Python](#getting_python) section and follow the instructions there.

## wxPython is not installed

If you only have the core packages installed with the Anaconda
distribution (plus the PmagPy package you just installed), you may get
the following ImportError when attempting to execute “eqarea.py -h”:

```
ImportError: No module named wx
```

To correct this error, execute at the command line:

```
pip install --upgrade -f https://wxpython.org/Phoenix/snapshot-builds/ wxPython
```

## Troubleshooting a pip install

If you installed with pip, but you have this error message or similar
when you try to run a program:

```
-bash: eqarea.py: command not found
```

Make sure you are running the [correct command](#which_command) for
your operating system and **PmagPy** install.

Once you have the correct command, if you still see that error message,
this probably means that you have not correctly installed PmagPy. On
your command line, try:

```
pip list
```

You should see both pmagpy-(version_number) and
pmagpy-cli-(version_number) on that list. If you don’t see them, go
ahead and reinstall:

```
pip install --upgrade --force-reinstall --no-cache-dir --no-deps pmagpy
pip install --upgrade --force-reinstall --no-cache-dir --no-deps pmagpy-cli
```

Fully uninstalling and reinstalling can occasionally fix other problems
as well!

## Troubleshooting a developer install

For more information on the developer install, you can run:

```
dev_setup.py -h
```

You can also check the specific [install
instructions](#getting_python).

For Mac users with a developer install, it is possible that you need to
make the python scripts executable. On the command line in the
PmagPy/programs directory, run the command: chmod a+x \*.py

### PATH for Windows

If you are trying to get a developer install to work on Windows, and you
want to set/check your \$PATH manually, see [Setting your Path in
Windows](http://www.mathworks.com/matlabcentral/answers/94933-how-do-i-set-my-system-path-under-windows).
More information about adding **PmagPy** to your \$PATH is available
[here](#setting_path).

### PATH for OSX or Linux

You can test if your PATH has been properly set with this command:

```
echo $PATH
```

If you don’t see PmagPy, PmagPy/programs, and
PmagPy/programs/conversion_scripts somewhere in the output, you have not
successfully completed a developer install.

If for some reason you need to add PmagPy to your \$PATH manually, you
can find more general information about setting \$PATH
[here](https://stackoverflow.com/questions/14637979/how-to-permanently-set-path-on-linux-unix),
and specific information about adding **PmagPy** to your \$PATH
[here](#setting_path).


## Problem with a PmagPy dependency

**PmagPy** depends on a variety of Python packages. Sometimes you will
run into problems if you have the wrong version of a dependency. You may
get an ImportError or a SyntaxError in these cases. You can check the
list of correct dependencies on
[Github](https://github.com/PmagPy/PmagPy/blob/master/environment.yml).

You can see what package versions you are running by using the command
“conda list” (or “pip list” if you have a non-Anaconda Python). You can
then compare with our list, and upgrade or downgrade if necessary. For
example: “conda install pandas=0.24.2”.

## Problems with a specific program

### Thellier auto_interpreter crashes with a Segmentation Fault (on Mac).

NB: This should no longer be a problem with matplotlib 2.0 and higher.

- This error is caused by a version issue with one of PmagPy’s
  dependencies, matplotlib. There are two ways to solve this problem.
- Recommended: upgrade matplotlib with the command “conda upgrade
  matplotlib”
- Alternative: download and use the [standalone Pmag
  GUI](#standalone) distribution to access Thellier GUI.

## Wrong Python in Jupyter notebook

If your jupyter notebook is calling the wrong version of python (i.e.,
using the OSX verion of python instead of Anaconda python), do this:

```
unlink /usr/local/bin/python
ln -s /Users/USERNAME/anaconda3/bin/python /usr/local/bin/python
```

and this:

```
unlink /usr/local/bin/pythonw
ln -s /Users/USERNAME/anaconda3/bin/pythonw /usr/local/bin/pythonw
```

where USERNAME is your username.


## Other problems

Report a problem not listed above on
[Github](https://github.com/PmagPy/PmagPy/issues/new). 
Please include the following information: 1) the
version of PmagPy that you are using, 2) your operating system, 3) any
error messages that you got, 4) the datafile that is giving trouble, if
relevant.
