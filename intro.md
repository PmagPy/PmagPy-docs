---
title: Books with Jupyter
---

# PmagPy: An open source package for paleomagnetic data analysis

PmagPy is a set of tools written in Python for the analysis of paleomagnetic data. It facilitates interpretation of demagnetization data, paleointensity data, and data from other types of rock magnetic experiments. PmagPy can be used to create a wide variety of useful plots. It is designed to work with the MagIC database (https://earthref.org/MagIC), allowing manipulation of downloaded data sets as well as preparation of new contributions for uploading to the MagIC database. It also supports the use of Jupyter notebooks for fully documented and nicely illustrated data analysis.

::::{grid} 1 1 2 3
:class-container: text-center
:gutter: 3

:::{grid-item-card}
:link: documentation_notebooks/PmagPy_introduction
:link-type: doc
:class-header: bg-light

Documentation notebooks ✏️
^^^

See PmagPy functions in action within these documentation notebooks
:::

:::{grid-item-card}
:link: documentation_notebooks/PmagPy_introduction
:link-type: doc
:class-header: bg-light

MyST Markdown ✨
^^^

Write MyST Markdown to create enriched documents with publication-quality features.

:::

:::{grid-item-card}
:link: content/executable/index
:link-type: doc
:class-header: bg-light

Executable content 🔁
^^^

Execute notebook cells, store results, and insert outputs across pages.

:::

:::{grid-item-card}
:link: interactive/launchbuttons
:link-type: doc
:class-header: bg-light

Live environments 🚀
^^^

Connect your book with Binder, JupyterHub, and other live environments
:::

:::{grid-item-card}
:link: publish/web
:link-type: doc
:class-header: bg-light

GUIs 🎁
^^^

Download and use Pmag GUI to analyze data and prepare data for MagIC
:::

:::{grid-item-card}
:link: content/components
:link-type: doc
:class-header: bg-light

UI components ⚡
^^^

Create interactive and web-native components and services.
:::

::::

This documentation is organized into a few major sections.

- **Tutorials** are step-by-step introductory guides to Jupyter Book.
- **Topic Guides** cover specific areas in more depth, and are organized as discrete "how-to" sections.
- **Reference** sections describe the API/syntax/etc of Jupyter Book in detail.

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
:link: contribute/intro.md
:class-header: bg-light

🙌 Contribute and raise issues

^^^

We welcome anyone to join us in improving PmagPy and helping one another learn as we conduct reproducible research in rock and paleomagnetism. You can do this be contributing code, improving documentation, or raising issues.

You can bring up issues you are having with PmagPy on our issues page (https://github.com/PmagPy/PmagPy/issues)

Check out our [contributing guide](https://github.com/PmagPy/PmagPy/blob/master/CONTRIBUTING.md) and please make contributions large or small.
:::

::::

# Analyzed with PmagPy

Below are some papers that have been conducted analysis with PmagPy.
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
:link: https://doi.org/10.1130/B32012.1/

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
:link: https://the-turing-way.netlify.app

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
:width: 200px
```

:::

:::{grid-item}
:columns: 7
Many thanks to the National Science Foundation, which [provides support for the MagIC database and PmagPy](https://www.nsf.gov/awardsearch/showAward?AWD_ID=2148719).
:::

::::

```{tableofcontents}
```
