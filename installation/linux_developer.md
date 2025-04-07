# Linux developer install

These are the install instructions for Linux/developer.

## Install Python

First, you will need to download a scientific Python distribution. We
strongly recommend Anaconda. Be warned, your computer comes with a
version of Python already installed; but this pre-installed version does
NOT have everything you will need to run **PmagPy**, so you will still
need to download Anaconda.

- Download and install [Anaconda Python
  3](https://www.anaconda.com/download).

- In general, if you run into errors with your Anaconda Python
  environment, it can save time to simply [uninstall and
  reinstall](https://docs.anaconda.com/anaconda/install/uninstall/).

- Open your command line (Terminal). See [this Cookbook
  section](https://earthref.org/PmagPy/cookbook/#command_line) for
  more information on finding your command line.

- Create and activate a new conda Python environment with some required
  packages:

  ```
  conda create -n pmagpy_env wxPython cartopy pandas matplotlib requests jupyter
  conda activate pmagpy_env
  pip install --user --upgrade pip setuptools
  conda install conda-forge::python-wget
  ```

- You have now created a new environment called “pmagpy_env” and
  activated it. This gives you a Python environment with the packages
  you need to run PmagPy programs. Each time you want to use PmagPy,
  you will open your Terminal and then run:

  ```
  conda activate pmagpy_env
  ```

  You can also deactivate the environment using:

  ```
  conda deactivate
  ```

  You must always activate your pmagpy environment when you open a new
  Terminal window if you want to use PmagPy in that window. To learn
  more about managing conda environments, etc., see the Anaconda
  documentation and
  [cheatsheet](https://know.continuum.io/rs/387-XNW-688/images/conda-cheatsheet.pdf).

- When running these commands you may see some warnings about
  dependencies, but you can just ignore them!

- If a package fails to install, you may need to use “sudo”: i.e.,
  `sudo pip install scripttest`. You will then be asked for your
  computer password.

## Install wxPython

Next, you need to install wxPython.

Most recently (on Ubuntu 18.04.2), I’ve had success with simply running:

```
conda install wxPython
```

However, in the past this didn’t work and still may not work for all
Linux distributions. Try the above command first, and if that fails, try
working through the instructions below.

- The following is a list of wxPython dependencies for Ubuntu 16.04
  (this list may be redundant or incomplete, depending on your specific
  OS):

  ```
  pip install libtiff

  sudo apt-get install libgtk-3-dev freeglut3-dev libgstreamer1.0-0 gstreamer1.0-plugins-base gstreamer1.0-plugins-good gstreamer1.0-plugins-bad gstreamer1.0-plugins-ugly gstreamer1.0-libav gstreamer1.0-doc gstreamer1.0-tools libgstreamer-plugins-base0.10-dev

  sudo apt-get install dpkg-dev build-essential libjpeg-dev  libtiff-dev libsdl1.2-dev   libnotify-dev  freeglut3 freeglut3-dev libsm-dev libwebkitgtk-3.0-dev libxtst-dev python-dev libpng-dev

  sudo apt-get install libwebkit2gtk-4.0-dev libsdl2-dev
  ```

  Carefully read through [this
  page](https://wxpython.org/pages/downloads/) and look for a
  compatible wheel for your distribution. Download the appropriate
  wheel and then install it:

  ```
  pip install wxPython-4.0.1-cp35-cp35m-linux_x86_64.whl
  ```

  Be sure to replace the wheel name above with the actual wheel you
  downloaded.

  Or install the wheel from the download site directly:

  ```
  pip install -U -f https://extras.wxpython.org/wxPython4/extras/linux/gtk3/ubuntu-16.04 wxPython
  ```

  Again, you will need the replace the link above with the link
  appropriate for your OS.

- If you aren’t able to find a wheel that works, try [these
  instructions](https://wxpython.org/blog/2017-08-17-builds-for-linux-with-pip/)

## Test your python

Run python on your command line.

You should see something like this:

```
Python 3.6.1 |Anaconda custom (x86_64)| (default, May 11 2017, 13:04:09)
[GCC 4.2.1 Compatible Apple LLVM 6.0 (clang-600.0.57)] on darwin
Type "help", "copyright", "credits" or "license" for more information.
>>>
```

If you don’t see that, go back and reinstall Anaconda.

Once you have successfully started the python interactive prompt, try:

```
import wx
```

You may have an error like this:

```
ImportError: libwx_gtk3u_core-3.0.so.0: cannot open shared object file: No such file or directory
```

If so, exit the python interpreter (quit()) and try:

```
export LD_LIBRARY_PATH=~/anaconda3/lib/python3.6/site-packages/wx/
```

(If you are using a non-Anaconda Python, your path to wx may be
different).

Try again to import wx. If it now works, you may want to add that line
to the end of your .bashrc file so that you don’t have to specify the
path each time.

For more details about this issue, see [this
explanation](https://github.com/wxWidgets/Phoenix/blob/e13273c5d939d993abf2a2649e90b3ea0d39382c/packaging/README-bdist.txt#L38-L57)
and [this Github issue](https://github.com/pyenv/pyenv/issues/691)
for more information.

## Install PmagPy

Here are the steps to clone and install **PmagPy**.

- You must use bash as your shell (not csh, zsh, etc.). You can make
  sure you are using bash with the command:

  ```
  printenv SHELL
  ```

  If your result is not “/bin/bash”, you will need to reset it. See
  [this
  question](https://stackoverflow.com/questions/13046192/changing-default-shell-in-linux)
  for more details.

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
  can be called from any directory. Try running:

  ```
  python dev_setup.py install
  ```

- If you have problems with the install, run `python dev_setup.py -h`
  for more information. You can also set your [PATH
  manually](https://earthref.org/PmagPy/cookbook/#setting_path) if
  dev_setup.py fails.

- After completing the developer install, you should restart your
  command line.

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

If you get an error about “pythonw”, you may need to link “python” to
“pythonw” with a command like:

```
ln -s ~/anaconda3/bin/python3 ~/anaconda3/bin/pythonw
```

If you get any other errors, or if any of the test commands don’t work,
go back and carefully follow the install instructions to make sure you
didn’t miss a step. If you still have a problem, try the
[Troubleshooting
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
