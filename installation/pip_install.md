# pip install

These are the install instructions for PmagPy. There are two main ways to install:

- The **recommended way** uses two tools — `conda` (which manages your Python environment) and `pip` (which installs PmagPy itself). This is the most reliable approach across macOS, Windows, and Linux, especially if you'll be using PmagPy regularly on your own computer.
- A **simpler way** uses only `pip`. This works well in cloud-based notebook environments like Google Colab, where the Python environment is already set up for you.

If you're not sure which to choose, go with the recommended way. Don't worry if some of the terms below are new — the steps are spelled out and you don't need a Python background to follow them.

(section_recommended_install)=
## Recommended approach: conda environment + pip install

This approach has two parts:

1. Create a clean Python environment using **conda**, with the larger scientific Python packages (NumPy, matplotlib, cartopy, etc.) installed up front.
2. Use **pip** to install `pmagpy` and `pmagpy-cli` on top.

Doing it this way avoids many of the install problems that come up when packages with native (non-Python) components — like cartopy and wxPython — are installed by pip alone. Conda handles those packages more reliably.

### Step 1: Install conda (if you don't have it)

If you don't already have a conda-based Python distribution on your computer, install one:

- [miniforge](https://github.com/conda-forge/miniforge) — a small, fast installer (recommended)
- [Anaconda](https://www.anaconda.com/download) — a larger distribution with a graphical installer

Either one provides the `conda` command you'll use below. You only need to do this once per computer.

### Step 2: Create a PmagPy environment

Open a terminal:

- macOS: open **Terminal**
- Linux: open **Terminal**
- Windows: open **Anaconda Prompt** (search for it in the Start menu)

Then run this command, which creates a new environment called `pmagpy_env` and installs the packages PmagPy needs:

```bash
conda create -n pmagpy_env -c conda-forge python=3.10 \
    numpy scipy matplotlib pandas \
    cartopy shapely \
    wxpython pyqt jupyterlab
```

This may take a few minutes the first time. The `-c conda-forge` part tells conda to use the conda-forge community package channel, which has the most reliable versions of these packages.

When it finishes, activate the environment:

```bash
conda activate pmagpy_env
```

Each time you open a new terminal window and want to use PmagPy, you'll need to run that `conda activate pmagpy_env` command again. To leave the environment, run `conda deactivate`.

### Step 3: Install PmagPy

With the `pmagpy_env` environment active, install PmagPy and its command-line tools from PyPI:

```bash
pip install --upgrade pmagpy
pip install --upgrade pmagpy-cli
```

That's it — PmagPy is installed.

(section_pure_pip_install)=
## Simpler alternative: pure pip

If you don't want to use conda — for example, you're working in Google Colab, JupyterHub, or a lightweight Python environment — you can install PmagPy with pip alone:

```bash
pip install --upgrade pmagpy[maps]
pip install --upgrade pmagpy-cli
```

The `[maps]` part adds support for making maps (cartopy and shapely). This works on most platforms but can occasionally hit problems on Linux, where cartopy needs system libraries that pip can't always install. If that happens, switch to the recommended conda approach above.

For a quick install in Google Colab where you don't need maps:

```python
!pip install pmagpy
```

## Test the install

Make sure your `pmagpy_env` environment is active (run `conda activate pmagpy_env` if it isn't), then type this in your terminal:

```bash
python -c "from pmagpy import pmag; print(pmag.angle([350.0,10.0],[320.0,20.0]))"
```

You should see something like `[30.59060998]` printed back.

To test the GUIs, with the environment active, run:

```bash
pmag_gui.py
```

The GUI may take 30 seconds or more to start the first time. If the window doesn't open, see the [troubleshooting page](troubleshooting.md).

## Platform notes

The steps above work on macOS, Windows, and Linux. The notes below cover a few platform-specific quirks worth knowing about.

### macOS

If you see this error when trying to launch a GUI:

```text
This program needs access to the screen.
Please run with a Framework build of python...
```

…use `pmag_gui_anaconda` (instead of `pmag_gui.py`) to launch the GUI. This is a long-standing macOS quirk for wxPython programs.

### Windows

- During Anaconda installation, choose "Just Me" rather than "All Users".
- Use the **Anaconda Prompt** (not the regular Command Prompt). Search for it in the Start menu.
- The GUI launcher on Windows is called `pmag_gui` (no `.py` at the end).

### Linux

The conda approach in step 2 above is strongly recommended on Linux. Installing wxPython through pip on Linux often runs into trouble because it needs several system libraries (graphics toolkit headers, etc.) and a wheel file specific to your Linux distribution. The conda-forge `wxpython` package handles all of this for you.

## Accessing example data files

PmagPy ships with example data files used in the documentation and in the textbook [Essentials of Paleomagnetism](http://earthref.org/MAGIC/books/Tauxe/Essentials/WebBook3.html). To copy them to your current working directory, navigate to the directory where you want them and run:

```bash
move_data_files.py
```

(If you have a [developer install](developer_install.md), the data files are already in the cloned repository at `PmagPy/data_files` and you don't need this step.)

## Keeping PmagPy up to date

To upgrade to the latest released version:

```bash
pip install --upgrade pmagpy
pip install --upgrade pmagpy-cli
```

To check what version you have installed:

```bash
pip show pmagpy
```

To uninstall:

```bash
pip uninstall pmagpy pmagpy-cli
```
