# Troubleshooting installation issues

## Verify Python is installed correctly

In a terminal, type `python` (or `python3`). You should see something like:

```text
Python 3.10.13 | packaged by conda-forge | (main, Oct 26 2023, 18:07:37)
[Clang 16.0.6 ] on darwin
Type "help", "copyright", "credits" or "license" for more information.
```

Press `Ctrl-D` (or type `quit()`) to exit. If you get an error like `command not found`, see the [pip install instructions](pip_install.md) for setting up Python via conda or miniforge.

## `ImportError: No module named wx` (or similar wxPython errors)

The PmagPy GUIs depend on wxPython. If it's missing, the cleanest fix is to install it from conda-forge into your active environment:

```bash
conda install -c conda-forge wxpython
```

On Linux specifically, conda-forge wxpython is by far the most reliable choice — pip-installed wxPython on Linux requires a long list of system libraries (`libgtk-3-dev`, `libgstreamer1.0-0`, etc.) and the right wheel for your distribution.

If you see `ImportError: libwx_gtk3u_core-3.0.so.0: cannot open shared object file` after a non-conda wxPython install, switch to the conda-forge package as above.

## `command not found` after a pip install

If you installed PmagPy with pip but get an error like:

```text
-bash: pmag_gui: command not found
```

…check that PmagPy and its CLI package are actually installed:

```bash
pip list | grep pmagpy
```

You should see both `pmagpy` and `pmagpy-cli`. If either is missing, install them:

```bash
pip install --upgrade pmagpy
pip install --upgrade pmagpy-cli
```

You may also need to use a different command name depending on your platform:

- macOS: `pmag_gui_anaconda` (or `pmag_gui.py`)
- Linux: `pmag_gui.py`
- Windows: `pmag_gui` (no `.py`)

If `pmag_gui.py` raises a `This program needs access to the screen. Please run with a Framework build of python` error on macOS, use `pmag_gui_anaconda`.

## `command not found` after a developer install

If you cloned the repo and did `pip install -e .` but the GUI commands aren't found from arbitrary directories, that's expected — `pip install -e .` only installs the `pmagpy` library, not the CLI commands. Two options:

- Navigate to the `programs/` directory in your clone and run the script directly: `cd PmagPy/programs && python pmag_gui.py`
- Install pmagpy-cli editably as well: from the PmagPy directory, run `python command_line_setup.py develop`. After that, `pmag_gui.py` (or the platform equivalent) works from any directory.

See the [developer install instructions](developer_install.md) for details on the three patterns.

## Mac-specific: scripts in `programs/` are not executable

For Mac users with a developer install, you may need to make the Python scripts executable:

```bash
cd PmagPy/programs
chmod a+x *.py
```

## Wrong version of a dependency

If you get an `ImportError` or unexpected behavior, you may have the wrong version of a dependency. Check what versions you have installed:

```bash
pip list
```

(or `conda list` if you installed dependencies via conda.) The expected runtime dependencies are listed in [`environment.yml`](https://github.com/PmagPy/PmagPy/blob/master/environment.yml) and in `setup.py`'s `install_requires`. Upgrade or downgrade as needed:

```bash
pip install 'pandas>=2.0'
```

## Wrong Python in Jupyter notebook

If your Jupyter notebook is calling the wrong Python interpreter (for example, system Python instead of the one in your conda environment), the cleanest fix is to install Jupyter inside the right environment:

```bash
conda activate pmagpy_env
conda install -c conda-forge jupyterlab
```

Then launch with `jupyter lab` from inside the activated environment. The kernel will use the active environment's Python.

If you specifically need to register an environment as a named kernel:

```bash
conda activate pmagpy_env
python -m ipykernel install --user --name pmagpy_env --display-name "PmagPy"
```

## Other problems

Report a problem not listed above on [GitHub](https://github.com/PmagPy/PmagPy/issues/new). Please include:

1. The version of PmagPy you are using (`pip show pmagpy`).
2. Your operating system.
3. The full error message and traceback.
4. The data file that is giving trouble, if relevant.
