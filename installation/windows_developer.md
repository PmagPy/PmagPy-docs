# Windows developer install

These are the install instructions for Windows/developer.

## Install Python

First, you will need to download a scientific Python distribution. We
strongly recommend Anaconda.

- Download and install [Anaconda Python
  3](https://www.anaconda.com/download). Select an install for “Just
  Me”, not for all users. You should select “Add Anaconda to my PATH
  environment variable” in Advanced Installation Options (if
  available). Otherwise, stick with the defaults.

- Open your command line (Command Prompt). See [this Cookbook
  section](https://earthref.org/PmagPy/cookbook/#command_line) for
  more information on finding your command line.

- Note: if you did not add Anaconda Python to your PATH as recommended
  above, you will open the “Anaconda Prompt” instead.

- Create and activate a new conda Python environment with some required
  packages:

  ```
  conda create -n pmagpy_env future cartopy pandas matplotlib requests jupyter
  conda activate pmagpy_env
  conda install scripttest --channel conda-forge --no-deps
  pip install --upgrade pip setuptools
  pip install wxpython
  ```

- You have now created a new environment called “pmagpy_env” and
  activated it. This gives you a Python environment with the packages
  you need to run PmagPy programs. Each time you want to use PmagPy,
  you will open your Command Prompt and then run:

  conda activate pmagpy_env

  You can also deactivate the environment using:

  conda deactivate

  You must always activate your pmagpy environment when you open a new
  Command Prompt window if you want to use PmagPy in that window. To
  learn more about managing conda environments, etc., see the Anaconda
  documentation and
  [cheatsheet](https://docs.anaconda.com/anaconda/user-guide/cheatsheet/).

## Test your python

To make sure that you have installed Python successfully, type
`python` on your command line. You should see something like this:

```
Python 3.6.4 |Anaconda custom (32-bit)| (default, Jan 16 2018, 10:21:59) [MSC v.1900 32 bit (Intel)] on win32
Type "help", "copyright", "credits" or "license" for more information.
>>>
```

(Type “quit()” and then hit enter to end your python session)

## Install PmagPy

Here are the steps to clone and install **PmagPy**.

- Open your command prompt [as an
  admin](http://www.thewindowsclub.com/how-to-run-command-prompt-as-an-administrator)
  (right click on the Command Prompt icon and select “Run as
  administrator”).

- Download and [install git](https://git-scm.com/downloads)

- Navigate to the directory where you want to put the PmagPy folder,
  then run:

  ```
  git clone https://github.com/PmagPy/PmagPy.git
  ```

- You should now have a full local copy of the PmagPy repository.
  Change directories into PmagPy:

  ```
  cd PmagPy
  ```

- Next, you need to add PmagPy to your PATH so that the PmagPy programs
  can be called from any directory. At present, you will have to do
  this manually. This section of the Cookbook has the full instructions
  for [editing your PATH for
  PmagPy](https://earthref.org/PmagPy/cookbook/#setting_path).

- After setting your PATH, you will need to restart the Command Prompt.
  After restarting, you should be able to use all **PmagPy**
  functionality. You will be able to stay up-to-date with **PmagPy**
  development and make edits in **PmagPy** code which will be
  immediately available in your system.

## Test PmagPy

Test core functionality:

- On your command line, type “python” to start the interpreter. You
  will import pmagpy and then run a simple calculation. Importing
  pmagpy may take over a minute the first time, so be patient! It will
  be much faster in subsequent runs.

  ```
  >>> from pmagpy import pmag
  >>> pmag.angle([350.0,10.0],[320.0,20.0])
  array([30.59060998])
  >>>
  ```

Test the GUIs:

- On the command line, open Pmag GUI by running:

  ```
  pmag_gui.py
  ```

Remember that the program may be very slow to initialize the first time!
You may also need to resize the GUI window. If the program doesn’t open
or you get an error message, go back and carefully follow the install
instructions to make sure you didn’t miss a step. If you still have a
problem, try the [Troubleshooting
section](https://earthref.org/PmagPy/cookbook/#trouble). If you don’t
find an answer there, check out the existing [Github
issues](https://github.com/PmagPy/PmagPy/issues) and create a new one
if necessary.

## Finishing up

Accessing example data files:

There are many data files used in the examples of programs and for use
with the textbook [Essentials of
Paleomagnetism](http://earthref.org/MAGIC/books/Tauxe/Essentials/WebBook3.html).
You can find these in PmagPy/data_files.

## Keeping PmagPy up-to-date

You will want to stay up to date with **PmagPy** development. To update
your developer install, you will just need to navigate to the **PmagPy**
directory and run:

```
git pull
```

This will grab all of the latest code from
[Github](https://github.com/PmagPy/PmagPy), and will be immediately
available to you.
