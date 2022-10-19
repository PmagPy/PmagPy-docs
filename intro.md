---
title: Books with Jupyter
---

# PmagPy: An open source package for paleomagnetic data analysis

PmagPy is a set of tools written in Python for the analysis of paleomagnetic data. It facilitates interpretation of demagnetization data, paleointensity data, and data from other types of rock magnetic experiments. The package is hosted on Github (https://github.com/PmagPy/PmagPy) and can be installed via PyPi (https://pypi.org/project/pmagpy/). PmagPy can be used to create a wide variety of useful plots. It is designed to work with the MagIC database (https://earthref.org/MagIC), allowing manipulation of downloaded data sets as well as preparation of new contributions for uploading to the MagIC database. It also supports the use of Jupyter notebooks for fully documented and nicely illustrated data analysis.

::::{grid} 1 1 2 3
:class-container: text-center
:gutter: 3

:::{grid-item-card}
:link: installation/osx_pip
:link-type: doc
:class-header: bg-light

Installation 🪴
^^^

Instructions for how to install PmagPy for your use case.

:::

:::{grid-item-card}
:link: documentation_notebooks/PmagPy_introduction
:link-type: doc
:class-header: bg-light

Documentation notebooks ✏️
^^^

See capabilities of PmagPy functions within these documentation Jupyter notebooks
:::

:::{grid-item-card}
:link: example_notebooks/example_notebooks
:link-type: doc
:class-header: bg-light

Example notebooks 📓
^^^

See example notebooks that analyze specific datasets using PmagPy.

:::

:::{grid-item-card}
:link: https://jupyterhub.earthref.org/
:class-header: bg-light

Live notebooks 🚀
^^^

Launch PmagPy notebooks on the Earthref JupyterHub.
:::

:::{grid-item-card}
:link: https://github.com/PmagPy/PmagPy-Standalone-OSX/releases/latest/
:class-header: bg-light

GUIs 🎁
^^^

Download and use Pmag GUI to analyze data and prepare data for MagIC
:::

:::{grid-item-card}
:link: https://www2.earthref.org/MagIC/
:class-header: bg-light

MagIC database ⚡
^^^

Develop new contributions and analyze existing datasets in the MagIC database.
:::

::::

PmagPy is comprised of:

- **Function modules for paleomagnetic data analysis** Function modules include that for paleomagnetic data analysis (pmagpy.pmag) and plotting (pmagpy.pmagplotlib) as well as interactive higher level data analysis (pmagpy.ipmag). The functions within these modules are at the heart of the GUI and command line programs. With pmagpy in the python path (which can be accomplished through pip installation ```pip install pmagpy```), these modules can be imported (e.g. ```import pmagpy.ipmag as ipmag```).
- **A graphical user interface (GUI) program** The PmagPy application enables users to get data into the MagIC database format as well as analyze demagnetization and paleointensity data.
- **Command line programs** The PmagPy command line programs enable all sorts of  paleomagnetic data analysis and wrangling. They are contained within the programs folder of the PmagPy repository (https://github.com/PmagPy/PmagPy) and can be pip installed (```pip install pmagpy-cli```).

# Citing PmagPy

Users of PmagPy should cite the open access article:

Tauxe, L., R. Shaar, L. Jonestrask, N. L. Swanson-Hysell, R. Minnett, A. A. P. Koppers, C. G. Constable, N. Jarboe, K. Gaastra, and L. Fairchild (2016), PmagPy: Software package for paleomagnetic data analysis and a bridge to the Magnetics Information Consortium (MagIC) Database, Geochem. Geophys. Geosyst., 17, doi:[10.1002/2016GC006307](http://dx.doi.org/10.1002/2016GC006307).

# Connect with us

We are an open source community that welcomes discussion, feedback, and contributions of many kinds.

::::{grid} 1 1 2 2
:class-container: text-center
:gutter: 3

:::{grid-item-card}
:class-header: bg-light

🌍 About our team

^^^

The code base for the PmagPy project has been built up over the years by Lisa Tauxe (<a href="https://github.com/ltauxe" class="user-mention">@ltauxe</a>; Professor Emrita at the Scripps Institution of Oceanography) and by Nicholas Swanson-Hysell (<a href="https://github.com/swanson-hysell" class="user-mention">@swanson-hysell</a>; Associate Professor at UC Berkeley) supported by grants from the National Science Foundation. Lori Jonestrask (<a href="https://github.com/moonshoes87" class="user-mention">@moonshoes87</a>) and Ron Shaar (<a href="https://github.com/ronshaar" class="user-mention">@ronshaar</a>, Senior Lecturer at the Hebrew University of Jerusalem) have made substantial contributions to the project as have others in the [open community of contributors](https://github.com/pmagpy/pmagpy/graphs/contributors). You too can become a contributor by putting in a pull request.
:::

:::{grid-item-card}
:class-header: bg-light

🙌 Contribute and raise issues

^^^

We welcome anyone to join us in improving PmagPy and helping one another learn as we conduct reproducible research in rock and paleomagnetism. You can do this be contributing code, improving documentation, or raising issues.

You can bring up issues you are having with PmagPy on our issues page (https://github.com/PmagPy/PmagPy/issues)

Check out our [contributing guide](https://github.com/PmagPy/PmagPy/blob/master/CONTRIBUTING.md) and please make contributions large or small.
:::

::::

# Analyzed with PmagPy

Below are just a few of the hundreds of papers that have been conducted analysis with PmagPy.
You can find more on [{bdg-primary}`Google Scholar`](https://scholar.google.com/scholar?cites=16152229079597538403).


::::{card-carousel} 3

:::{card}
:margin: 3
:class-body: text-center
:class-header: bg-light text-center
:link: https://www.nature.com/articles/s41550-021-01469-y
**Moon rocks**
^^^
```{image} images/example_papers/Nichols_2021.png
:height: 100
```

Nature Astronomy: The palaeoinclination of the ancient lunar magnetic field from an Apollo 17 basalt
+++
Explore this paper {fas}`arrow-right`
:::

:::{card}
:margin: 3
:class-body: text-center
:class-header: bg-light text-center
:link: https://doi.org/10.1130/B32012.1

**Supercontinents**
^^^
```{image} images/example_papers/Eyster_2020.png
:height: 100
```

GSAB: Paleomagnetism of the Chuar Group...with implications for the makeup and breakup of Rodinia
+++
Explore this paper {fas}`arrow-right`
:::

:::{card}
:margin: 3
:class-body: text-center
:class-header: bg-light text-center
:link: https://doi.org/10.1029/2018GC007509

**Ancient fields**
^^^
```{image} images/example_papers/Jones_2020.png
:height: 100
```

G^3: Archeointensity of the Four Corners Region of the American Southwest
+++
Explore this paper {fas}`arrow-right`
:::

# Acknowledgements

::::{grid} 2 2 2 2

:::{grid-item}
:columns: 4

```{image} https://www.nsf.gov/policies/images/NSF_Official_logo_High_Res_1200ppi.png
:class: m-auto
:width: 150px
```

:::

:::{grid-item}
:columns: 7
Many thanks to the National Science Foundation, which [provides support for the MagIC database and PmagPy](https://www.nsf.gov/awardsearch/showAward?AWD_ID=2148719).
:::

::::
