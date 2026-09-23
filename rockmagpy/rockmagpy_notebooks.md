# RockmagPy notebooks

The `pmagpy.rockmag` module (RockmagPy) provides functions for processing and interpreting rock magnetic experiments. It is documented through a separate collection of Jupyter notebooks, rendered as a website at

👉 **https://pmagpy.github.io/RockmagPy-notebooks**

with the notebooks themselves in the [RockmagPy-notebooks repository](https://github.com/PmagPy/RockmagPy-notebooks). The notebooks work from MagIC-format measurement tables, so the same workflow applies to data downloaded from MagIC and to new data being prepared for contribution. The functions are also listed in the [API Reference](../api/api) on this site.

```{admonition} Under active development
:class: warning
RockmagPy is under active development. Function names, arguments, and outputs may change; backward compatibility is not guaranteed for `pmagpy.rockmag` at this time.
```

## What is there

- **Nuts and bolts** — getting started, and unpacking a MagIC contribution into the tables the notebooks use.
- **Hysteresis and backfield** — processing of hysteresis loops following the protocol of Jackson and Solheid (2010): symmetry-based centering and quality statistics, drift correction, a loop-closure statistic, high-field linearity tests, and linear or approach-to-saturation fitting for $\chi_{HF}$ and $M_s$, in batch and as a step-by-step walk-through; backfield (remanent coercivity) curves; coercivity unmixing by least squares and by a Bayesian approach; and Day, Néel and squareness–coercivity summary plots.
- **FORC diagrams** — first-order reversal curve processing, smoothing (including variable smoothing after VARIFORC), and plotting.
- **Low-temperature (MPMS) experiments** — DC remanence on cooling and warming (RTSIRM, FC/ZFC), AC susceptibility, estimation of the Verwey transition temperature, goethite fitting, and a signal blender for building intuition about mixed assemblages.
- **Thermomagnetic experiments** — high-temperature susceptibility and Curie temperature estimation.
- **Anisotropy** — anisotropy of magnetic susceptibility plots, with background on the tensor and its parameters.
- **Rock Magnetic Bestiary** — notebooks that process reference materials measured at the Institute for Rock Magnetism (e.g. siderite, the titanomagnetite series), for comparison with natural samples.
- **API reference** — a reference sheet for the `pmagpy.rockmag` functions used throughout the notebooks.

## Running the notebooks

The notebooks can be run on the [EarthRef JupyterHub](https://jupyterhub.earthref.org/) or locally with PmagPy installed (see [Installation](../installation/PmagPy_install.md)); several depend on optional packages listed in the RockmagPy-notebooks repository.
