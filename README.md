# PmagPy-docs

At the moment, this repository is an experiment to generate a Jupyter-Book from PmagPy notebooks.

Jupyter book can be installed via pip:
```
pip install -U jupyter-book
```

With Jupyter book installed, the Jupyter book in this repository can be made with this command:
```
jupyter-book build PmagPy-docs
```

The resulting html can be published to github pages using this directions:

https://jupyterbook.org/en/stable/publish/gh-pages.html

```
ghp-import -n -p -f _build/html
```
