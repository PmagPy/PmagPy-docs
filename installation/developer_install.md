# Developer install

A developer install lets you work directly from the PmagPy source code on your computer: edits to the code take effect immediately, you can switch between branches, and you can stay current with the latest changes between releases. Use this install path if you want to contribute to PmagPy or follow development closely.

If you only want to use PmagPy as a library and don't need the latest unreleased changes, the [pip install](pip_install.md) page covers the simpler workflow.

## Recommended approach

The same three-step pattern works on macOS, Windows, and Linux:

1. Create a conda environment with the scientific Python packages and GUI libraries.
2. Clone the PmagPy repository.
3. Install pmagpy as an *editable* package with `pip install -e .` so your imports point at the cloned repo.

### Step 1: Create a conda environment

If you don't already have a conda-based Python distribution, install [miniforge](https://github.com/conda-forge/miniforge) (recommended) or [Anaconda](https://www.anaconda.com/download).

Create a fresh environment with the dependencies that benefit most from conda-forge:

```bash
conda create -n pmagpy_dev -c conda-forge python=3.10 \
    numpy scipy matplotlib pandas \
    cartopy shapely \
    wxpython pyqt jupyterlab
conda activate pmagpy_dev
```

### Step 2: Clone PmagPy

If you don't have git, [install it](https://git-scm.com/downloads) first. Then change to the directory where you want the PmagPy folder, and clone:

```bash
git clone https://github.com/PmagPy/PmagPy.git
cd PmagPy
```

You now have a full local copy of the PmagPy source.

### Step 3: Install in editable mode

From the PmagPy directory:

```bash
pip install -e .[maps]
```

The `-e` flag installs PmagPy as an *editable* package — Python imports from your cloned repo directly, so any code changes (or `git pull`) take effect immediately without reinstalling. The `[maps]` part adds cartopy and shapely; you can drop it if you already installed those via conda above and would like pip to leave them alone.

## Running the command-line programs

There are three patterns for using the command-line programs (`pmag_gui.py`, `magic_gui.py`, `demag_gui.py`, `thellier_gui.py`, the conversion scripts, etc.) after a developer install. Pick the one that fits your workflow.

### Pattern A: Navigate and run (simplest)

If you mostly edit library code and only occasionally launch the GUIs, just `cd` into the `programs/` directory and run them:

```bash
cd /path/to/PmagPy/programs
python pmag_gui.py
```

No second install, no PATH changes. This is a fine default for most contributors.

### Pattern B: Editable install of pmagpy-cli

To make `pmag_gui.py`, `magic_gui.py`, etc. available as commands from anywhere, install pmagpy-cli editably as well. From the PmagPy directory:

```bash
python command_line_setup.py develop
```

(`pip install -e .` doesn't work here because pip only looks at `setup.py`, while pmagpy-cli is built from `command_line_setup.py`. The `setup.py develop` form is the older editable-install command that pip's `-e` was originally built around — it still works.)

After this, the GUI launchers and command-line conversion scripts work from any directory and reflect your edits to `programs/` and `dialogs/` immediately.

### Pattern C: Editable library + released CLI

If you only edit library code (not the GUIs), you can have an editable install of the library *and* the released CLI side by side:

```bash
pip install -e .[maps]
pip install pmagpy-cli
```

This is the cleanest separation when you're not touching `programs/` or `dialogs/`.

## Test the install

Make sure your `pmagpy_dev` environment is active (run `conda activate pmagpy_dev` if it isn't). Then test core library functionality:

```bash
python -c "from pmagpy import pmag; print(pmag.angle([350.0,10.0],[320.0,20.0]))"
```

You should see something like `[30.59060998]`.

To test the GUIs, with the environment active, run:

```bash
pmag_gui.py
```

(On macOS, if `pmag_gui.py` raises a `This program needs access to the screen` error, try `pmag_gui_anaconda` instead. If you used Pattern A above, `cd` into `PmagPy/programs` first.)

## Keeping a developer install up to date

From the PmagPy directory:

```bash
git pull
```

Because the install is editable, the next `import pmagpy` will use the updated code — no reinstall needed. The exception is when `setup.py` itself changes (for example, new dependencies are added), in which case rerun:

```bash
pip install -e .[maps]
```

## Working with branches

To test a feature branch, work on a contribution, or reproduce a bug against `master`:

```bash
git checkout <branch-name>
```

Your editable install will now import from that branch's code. Switching branches needs no reinstall.

## Platform notes

### macOS

- Both bash and zsh work as the shell. zsh has been default since macOS Catalina.
- The wxPython-based GUI launchers may need to be invoked as `pmag_gui_anaconda` rather than `pmag_gui.py` if you see a "needs access to the screen" / Framework build error.

### Windows

- During Anaconda installation, choose "Just Me" rather than "All Users".
- Use the **Anaconda Prompt** rather than the regular Command Prompt if `conda activate` doesn't work.
- The GUI launcher on Windows is `pmag_gui` (no `.py` suffix).

### Linux

- The conda-forge `wxpython` package (already covered in step 1 above) is by far the most reliable way to get a working GUI stack on Linux. Pip-installed wxPython on Linux historically requires a long list of system libraries (`libgtk-3-dev`, `libgstreamer1.0-0`, etc.) and a wheel file specific to your Linux distribution.
- If you see `ImportError: libwx_gtk3u_core-3.0.so.0: cannot open shared object file` after a non-conda wxPython install, switch to the conda-forge package.

## Note on dev_setup.py

Older PmagPy documentation referenced a `dev_setup.py` script that adds the cloned repo's `programs/` and `programs/conversion_scripts/` directories to your shell `PATH` and adds the repo root to `PYTHONPATH` by editing `~/.bashrc` / `~/.bash_profile` / `~/.profile`. This script still exists in the repository and still works, but it predates the modern `pip install -e .` approach above and is no longer the recommended way. The patterns above (especially Pattern A or B for running the CLI tools) accomplish the same goal more cleanly.

## See also

- [pip install](pip_install.md) — for the simpler non-developer install.
- [troubleshooting](troubleshooting.md) — for common installation issues.
- [PmagPy contributing guide](https://github.com/PmagPy/PmagPy/blob/master/CONTRIBUTING.md) — once you're set up to contribute.
