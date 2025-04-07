# Jupyter Notebooks

Jupyter Notebooks
EarthRef's JupyterHub Server
EarthRef.org supports a JupyterHub server where you can run PmagPy notebooks and create your own. Login using your EarthRef(MagIC) username(handle) and password. If you don't know your EarthRef username and password, login to the MagIC website at the home page. You can login using your ORCID id or your username and password, or create an account with your ORCID id. You can then view, set, or edit your username and password by clicking on your name in the upper right of the webpage. If you created your account with an ORCID id, you will have to set your username and password before logging into the JupyterHub.

The JuypterHub site can be found at jupyterhub.earthref.org.

PmagPy Fundemetals
A Juypter Notebook explaining PmagPy Online. This is a tutorial on using the EarthRef JuypterHub, PmagPy, and the MagIC database.
A presentation of the notebook by Lisa Tauxe at the EarthCube 2020 meeting can be found at doi.org/10.1002/essoar.10504182.1.

These five Jupyter notebooks for PmagPy can also be downloaded separately and describes many of the functions and uses of the PmagPy in more detail. They can be downloaded from the PmagPy GitHub website:
Introduction
PmagPy and MagIC
Calculations
Plots and Analysis
PmagPy - Command Line Versions of PmagPy Functions

Other PmagPy Notebooks
2020 MagIC Workshop PmagPy Jupyter Notebook Tutorial
This notebook covers how to use PmagPy in three parts. Exercise 1 looks at a typical "directional" data set and shows how to make useful plots like the equal area projection, maps of VGPs and maps of site locations. Exercise 2 shows how to get geomagnetic vectors from IGRF-like tables and several ways of looking at the data through time and space. Exercise 3 considers directional (polarity), anisotropy data and natural gamma radiation (NGR), a measure of the dominance of clay versus diatomaceous ooze in this core, as a function of depth in an IODP core.
Demo recording on YouTube: PmagPy Using Jupyter Notebooks

Tauxe el al. (2016) PmagPy Example Notebooks 
Python Jupyter Notebooks from the 2016 G-Cubed paper describing PmagPy. Includes a notebook for taking two data sets from the MagIC database and conducting a variety of analyses on them including a fold test, a common mean test and the calculation of a combined paleomagnetic pole. This collection also includes a variety of shorter code examples that put PmagPy functions to use within the notebook environment.

2017 MagIC Workshop PmagPy Tutorial
Python Jupyter Notebooks from the 2017 MagIC Workshop by Nick Swanson-Hysell. Includes updated notebooks from the Tauxe et al. (2016) along with other notebooks.

Data analysis in Python benefits from an increasingly robust ecosystem
of packages for scientific computing and plotting. The Jupyter notebook
is one such tool. It has gained widespread use for conducting and
presenting data analysis. Jupyter builds on the IPython project which
began as a way to bring increased interactivity to data analysis in
Python {raw-latex}`\citep{perez07}` and has evolved to include an
interactive notebook environment that seeks to enable the full
trajectory of scientific computing from initial analysis and
visualization, to collaboration, and through to publication. The project
has expanded to enable a reproducible interactive computing environment
for many other programming languages (such as R and Julia) and the
language-agnostic parts of its architecture are known
as Project Jupyter (<http://jupyter.org>). Jupyter notebooks allow for
executable code, results, text and graphical output to coherently
coexist in a single document. With these combined components, they are
excellent tools both for conducting data analysis and presenting
results.

To show some of what is possible in terms of data analysis using
**PmagPy** in a notebook environment, we have created example notebooks
that illustrate project workflows as well as notebooks that document
many different **PmagPy** functions.



that are available for download from this repository:
<https://github.com/PmagPy/2016_Tauxe-et-al_PmagPy_Notebooks>. These
notebooks can also be viewed as static webpages here:
<http://pmagpy.github.io/Example_PmagPy_Notebook.html> and
<http://pmagpy.github.io/Additional_PmagPy_Examples.html>.

The main example notebook (Example_PmagPy_Notebook.ipynb) combines data
from two different studies for the sake of developing a mean
paleomagnetic pole from the upper portion of a sequence of volcanics in
the North American Midcontinent Rift
{raw-latex}`\citep{halls74, swansonhysell14}`. The two data files used
within the notebook can be downloaded from the MagIC database. The
digital object identifier (doi) search option allows for the data files
to be readily located as <https://earthref.org/MagIC/doi/10.1139/e74-113/>
and <https://earthref.org/MagIC/doi/10.1002/2013GC005180/>. Downloading
these data files from the database and putting them into folders within
a local ‘Project Directory’ allows them to be accessed within the
Jupyter notebook.

Within the example notebook, these data are unpacked into their
respective MagIC formatted tab delimited data files. The data are then
loaded into dataframes and filtered using several different criteria
(stratigraphic height and polarity). Several functions from the
**ipmag** module are used for making equal area projections and
calculating statistics. In addition to combining the data sets to
calculate the mean pole, the code in the notebook conducts a bootstrap
fold test on the data using the approach of {raw-latex}`\cite{tauxe94}`
as well as a common mean test. The data recombinations and calculations
done in this notebook are examples of portions of the data analysis
workflow which are often difficult to document and reproduce. The
examples illustrate a small sliver of the potential for the use of
notebooks for data manipulation and analysis of paleomagnetic data.
Additional functionality available within PmagPy is demonstrated within
the additional **PmagPy** examples notebook
(Additional_PmagPy_Examples.ipynb) as small vignettes of example code.
Functions related to paleomagnetic and rock magnetic data analysis are
shown as examples. The notebook also illustrates some of the
interactivity that can be built into the notebook utilizing IPython
widgets.

If you want to to run the example notebook interactively, you’ll need to
follow these steps:

1. [Install Python and PmagPy](#getting_python)

2. [Download git](https://git-scm.com/downloads)

3. Open your [command line](#command_line)

4. Clone the notebook repository:

   ```
   git clone https://github.com/PmagPy/2016_Tauxe-et-al_PmagPy_Notebooks

   cd 2016_Tauxe-et-al_PmagPy_Notebooks

   jupyter notebook
   ```

This will open up a local IPython server in your default web browser.
Click on *Example_PmagPy_notebook.ipynb* to open and edit the main
example notebook. You will see something like this:

```{image} ../images/documentation_notebooks/notebook.jpg
:alt: image
:width: 15cm
```

Notebooks are constructed as a series of ‘cells’ which can be text or
code. To view the ‘source’ of a text cell, just click on it. To render
it, click on the ‘run’ button (sideways triangle on the toolbar).
Similarly, to run the code in a code cell, click on the cell and then
the ‘run’ button (or use the shift+enter short cut). To execute the
entire notebook, click on the ‘Cell’ button and choose ’Run All’.

Now you are ready to look at some data. In the code block under the
heading ‘Reading data from MagIC format results files’, data are read in
from a file [downloaded](#magic_download) and unpacked from the MagIC
database. The notebook shows how to read in the data into a [pandas
DataFrame](#pandas), and plot the directions on an equal area
projection:

```{image} ../images/documentation_notebooks/SnakeRiver.jpg
:alt: image
:width: 15cm
```

There are several other tricks shown off in the notebook, which should
be enough to get you started using **ipmag** in a Python notebook
environment. Conducting data analysis using **PmagPy** in a notebook
allows for the underlying code of statistical tests to be available and
for the decisions made in the specific implementation of such tests to
be transparently presented.

Although there is much much more to do in Python, this documentation is
aimed at getting and using **PmagPy**, so that’s it for this chapter.
Congratulations if you made it to the end!
