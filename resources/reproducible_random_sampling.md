# Reproducible random sampling in PmagPy

Many **PmagPy** functions involve random number generation — drawing directions from a Fisher distribution, bootstrap resampling, Monte Carlo simulations, and generating synthetic datasets from the TK03.GAD secular variation model. By default, these functions produce different results each time they are called. The optional `random_seed` parameter makes any of these analyses exactly reproducible.

## Quick start

Pass an integer to `random_seed` and the output is deterministic:

```python
import pmagpy.ipmag as ipmag

# Two calls with the same seed produce identical results
data_a = ipmag.fishrot(k=30, n=50, dec=0, inc=45, random_seed=42)
data_b = ipmag.fishrot(k=30, n=50, dec=0, inc=45, random_seed=42)
# data_a and data_b are identical

# Without random_seed (or random_seed=None), each call gives different results
data_c = ipmag.fishrot(k=30, n=50, dec=0, inc=45)
data_d = ipmag.fishrot(k=30, n=50, dec=0, inc=45)
# data_c and data_d differ
```

## Functions that accept `random_seed`

### ipmag (high-level, notebook-friendly)

| Function | Purpose |
| --- | --- |
| `fishrot` | Fisher-distributed random directions |
| `fisher_mean_resample` | Resample directions from a Fisher mean |
| `kentrot` | Kent-distributed random directions |
| `tk03` | TK03.GAD statistical field model |
| `bootstrap_fold_test` | Bootstrap fold test (Tauxe and Watson, 1994) |
| `mean_bootstrap_confidence` | Bootstrap confidence region for a mean direction |
| `common_mean_bootstrap` | Bootstrap test for a common mean |
| `common_mean_bootstrap_H23` | Bootstrap common mean test (Heslop et al., 2023) |
| `common_mean_watson` | Watson common mean test with Monte Carlo |
| `reversal_test_bootstrap` | Bootstrap reversal test |
| `reversal_test_bootstrap_H23` | Bootstrap reversal test (Heslop et al., 2023) |
| `find_svei_kent` | Secular variation of the Earth's magnetic field |
| `find_ei` | Elongation/inclination inclination-shallowing correction with bootstrap |
| `find_ei_kent` | E/I correction with a Kent confidence ellipse on the corrected pole |
| `find_compilation_kent` | Pole correction by resampling a compilation of flattening factors |
| `reversal_test_MM1990` | McFadden and McElhinny (1990) reversal test with Monte Carlo critical values |
| `simul_correlation_prob` | Bogue and Coe (1981) probabilistic correlation via simulation |
| `rand_correlation_prob` | Bogue and Coe (1981) probabilistic correlation via random directions |
| `plate_rate_mc` | Monte Carlo plate rate estimation |

### pmag (low-level)

| Function | Purpose |
| --- | --- |
| `fshdev` | Fisher-distributed deviate (scalar or array kappa) |
| `kentdev` | Kent-distributed deviate |
| `gaussdev` | Gaussian random samples |
| `get_unf` | Uniformly distributed random directions |
| `pseudo` | Bootstrap resample of a directional dataset |
| `pseudosample` | Bootstrap resample of a generic list |
| `di_boot` | Bootstrap means for directional data |
| `dir_df_boot` | Bootstrap means for a directional DataFrame |
| `apseudo` | Bootstrap resample of anisotropy tensors |
| `s_boot` | Bootstrap parameters for anisotropy data |
| `scalc_vgp_df` | VGP scatter (Sf) with bootstrap or within-site correction |
| `mktk03` | Generate Gauss coefficients from TK03 |

## Sharing a single RNG across multiple calls

When calling a random function inside a loop, create a single `numpy.random.Generator` object and pass it through each call. This advances the random state sequentially so that every draw is different but the full sequence is reproducible:

```python
import numpy as np
import pmagpy.pmag as pmag

rng = np.random.default_rng(42)

fish = []
for i in range(100):
    d, i = pmag.fshdev(20, random_seed=rng)
    fish.append([d, i])
```

````{admonition} Avoid passing an integer seed inside a loop
:class: warning
Passing the same integer to `random_seed` inside a loop reseeds the generator on every iteration, producing identical draws:

```python
# WRONG — every iteration gives the same direction
for i in range(100):
    d, i = pmag.fshdev(20, random_seed=42)  # same seed each time!
```

Create the Generator once outside the loop and pass it in.
````

## How it works

The `random_seed` parameter accepts three types of input:

| Input | Behavior |
| --- | --- |
| `None` (default) | Fresh entropy on every call — non-reproducible, same as previous **PmagPy** behavior |
| `int` | Creates a seeded `numpy.random.Generator` — deterministic and reproducible |
| `numpy.random.Generator` | Uses the provided Generator directly — for threading RNG state through call chains |

Internally, **PmagPy** uses the modern `numpy.random.Generator` API (`numpy.random.default_rng`) rather than the legacy `numpy.random.seed` approach. This means:

- No global state is modified — setting `random_seed` in one function cannot affect other unrelated code.
- Multiple seeded analyses can run concurrently without interfering with each other.
- The default behavior (`random_seed=None`) is identical to previous **PmagPy** versions.

## Examples

### Reproducible Fisher directions

```python
data = ipmag.fishrot(k=50, n=200, dec=340, inc=60, random_seed=99)
ipmag.plot_net(1)
ipmag.plot_di(di_block=data)
```

### Reproducible bootstrap common mean test

```python
data1 = ipmag.fishrot(k=40, n=20, dec=40, inc=60, random_seed=0)
data2 = ipmag.fishrot(k=45, n=20, dec=42, inc=58, random_seed=1)
result = ipmag.common_mean_bootstrap(data1, data2, random_seed=2)
```

### Reproducible TK03.GAD secular variation model

```python
directions = ipmag.tk03(n=500, dec=0, lat=45, rev='no', random_seed=7)
```

### Sharing RNG state across a custom analysis

```python
rng = np.random.default_rng(0)

# Generate synthetic data
data1 = ipmag.fishrot(k=50, n=30, dec=0, inc=60, random_seed=rng)
data2 = ipmag.fishrot(k=50, n=30, dec=5, inc=58, random_seed=rng)

# Run a bootstrap test — same rng continues the sequence
result = ipmag.common_mean_bootstrap(data1, data2, random_seed=rng)
```

The entire sequence above is deterministic because a single Generator threads through all three calls.
