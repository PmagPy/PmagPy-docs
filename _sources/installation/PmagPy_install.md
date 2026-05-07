# Installing **PmagPy**

You have several options for using PmagPy, depending on what you want to do with it.

- If you only want the graphical user interfaces (GUIs) — [Pmag GUI](../programs/pmag_gui.md), [Demag GUI](../programs/demag_gui.md), and [Thellier GUI](../programs/thellier_gui.md) — without the rest of PmagPy's functionality, you can download a standalone application that doesn't require Python (see [](section_Standalone_GUI)).

- If you want the full PmagPy library, the [command-line programs](../programs/command_line_programs.md), and the ability to use PmagPy in Jupyter notebooks, do a [pip install](pip_install.md).

- If you want to actively contribute to PmagPy or follow the latest commits between releases, do a [developer install](developer_install.md) from a local clone of the repository.

You can also use PmagPy without installing anything by going to the Jupyter notebooks hosted at the EarthRef JupyterHub:

- If you don't have an EarthRef account, go to <https://earthref.org/log-in> and create one with your ORCID. (If you don't have an ORCID, you can create one there too.)
- Once logged in, go to <https://jupyterhub.earthref.org> and log in with your EarthRef account.
- Click on the `PmagPy Online - Setup.ipynb` link and follow the instructions.
- To learn more about Jupyter notebooks and Python, the [Python for Earth Sciences](https://github.com/ltauxe/Python-for-Earth-Science-Students) class is a good starting point.

(section_pip_install)=
## pip install

If you already have a working Python environment on your computer or in a cloud environment like Google Colab, you can install PmagPy with:

```bash
pip install pmagpy
```

Or, to also get the optional mapping libraries (cartopy and shapely) for map-making functions:

```bash
pip install pmagpy[maps]
```

To get the associated command-line programs, install `pmagpy-cli`:

```bash
pip install pmagpy-cli
```

For guidance on getting set up a Python environment with the necessary dependencies, the [pip install](pip_install.md) page walks through the recommended approach (`conda` for the scientific Python packages, then `pip` for PmagPy on top) along with notes for macOS, Windows, and Linux.

(section_Standalone_GUI)=
## Standalone GUI download

If you only want to use Pmag GUI, MagIC GUI, Thellier GUI, and Demag GUI, you can download a standalone application that doesn't require Python.

- macOS: <https://github.com/PmagPy/PmagPy-Standalone-OSX/releases/latest>
- Windows: <https://github.com/PmagPy/PmagPy-Standalone-Windows/releases/latest>

Standalone GUI binaries are available only for macOS and Windows. Linux users should use the [pip install](pip_install.md) instead — it works smoothly on Linux when combined with conda for the GUI dependencies.

(section_developer_install)=
## PmagPy developer install

If you want to work directly from the current code in the repository — to contribute, follow development between releases, or test a feature branch — do a [developer install](developer_install.md).

If you have an existing pip install in the same Python environment, uninstall it first to avoid conflicts:

```bash
pip uninstall pmagpy pmagpy-cli
```

## Getting help

If you run into trouble during installation, see the [troubleshooting](troubleshooting.md) page.

To report a bug or request a feature, open a [GitHub issue](https://github.com/PmagPy/PmagPy/issues). For broader contribution questions, including how to submit pull requests, see the [contribution guidelines](https://github.com/PmagPy/PmagPy/blob/master/CONTRIBUTING.md).

## Next steps

Once you have PmagPy installed:

- [Learn more about the **MagIC** database and download data.](../MagIC/MagIC.md)
- [Analyze and/or upload demagnetization](../programs/demag_gui.md) and/or paleointensity measurement data to the **MagIC** database.
- [Learn how to write your own programs in Python.](../resources/survival_skills.md)
- [Learn how to use Jupyter notebooks for managing your data analysis workflow.](../documentation_notebooks/PmagPy_introduction.ipynb)
- [Learn more about command-line programs in the **PmagPy** software package.](../programs/command_line_programs.md)
