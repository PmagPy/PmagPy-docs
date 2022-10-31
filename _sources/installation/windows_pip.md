# Windows pip install

These are the install instructions for Windows/pip.

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
  more information on finding Command Prompt)

- Note: if you did not add Anaconda Python to your PATH as recommended
  above, you will open the “Anaconda Prompt” instead).

- Create and activate a new conda Python environment with some required
  packages:

  ```
  conda create -n pmagpy_env future wxPython cartopy pandas matplotlib requests jupyter
  conda activate pmagpy_env
  pip install --user --upgrade pip setuptools
  conda install conda-forge::python-wget
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
  [cheatsheet](https://know.continuum.io/rs/387-XNW-688/images/conda-cheatsheet.pdf).

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

- Install pmagpy and pmagpy-cli into your pmagpy_env:

  ```
  pip install --upgrade pmagpy --no-deps
  pip install --upgrade pmagpy-cli --no-deps
  ```

- If you are getting weird install errors, try uninstalling and then
  force reinstalling with this:

  ```
  pip uninstall pmagpy pmagpy-cli
  pip install pmagpy --upgrade --no-deps --force-reinstall --no-cache-dir
  pip install pmagpy-cli --upgrade --no-deps --force-reinstall --no-cache-dir
  ```

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
  pmag_gui
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
You may want to copy the data files to your Desktop or another
convenient location. To do this, navigate on the command line to your
desired destination folder (for help, see [this Cookbook
section](https://earthref.org/PmagPy/cookbook/#file_system)). Then,
use the command:

```
move_data_files
```

This will copy all of the PmagPy example files to your current
directory. NB: If you have a developer install, you can simply navigate
to PmagPy/data_files, and move_data_files will not be needed.

## Keeping PmagPy up-to-date

To stay up to date with new features and bug fixes, you should
periodically update both **PmagPy** packages.

```
pip install pmagpy --upgrade --no-deps
```

To check the currently installed version number for pmagpy (or any other
Python package), run:

```
conda list
```

If you ever need to uninstall pmagpy or pmagpy-cli:

```
pip uninstall pmagpy
```

or

```
pip uninstall pmagpy-cli
```
