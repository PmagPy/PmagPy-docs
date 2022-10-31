# PmagPy-docs

This repository generates this Jupyter Book website: https://pmagpy.github.io/PmagPy-docs/

Jupyter book can be installed via pip:
```
pip install -U jupyter-book
```

With Jupyter book installed, the Jupyter book in this repository can be made with this command:
```
jupyter-book build PmagPy-docs
```

To keep the repository from getting humongous. The current approach is to build the html locally using the above command, but not to push the changes in the resulting `_build` folder. 

The resulting html after a local build can be published to github pages using these directions:

https://jupyterbook.org/en/stable/publish/gh-pages.html

and specifically this command from within the ```main``` branch:

```
ghp-import -n -p -f _build/html
```
