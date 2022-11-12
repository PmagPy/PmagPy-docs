# PmagPy-docs

This repository generates this Jupyter Book website: https://pmagpy.github.io/PmagPy-docs/

# Developing the book content and deploying the book

## Installing Jupyter Book

Jupyter book can be installed via pip:
```
pip install -U jupyter-book
```

## Building the Jupyter Book

With Jupyter book installed, the Jupyter book in this repository can be made with this command. To run this command you need to be not in the directory itself, but in the directory that contains the folder:
```
jupyter-book build PmagPy-docs
```

To keep the repository from getting humongous. The current approach is to build the html locally using the above command, but not to push the changes in the resulting `_build` folder. 

## Deploying the Jupyter Book

The resulting html after a local build can be published to github pages using these directions:

https://jupyterbook.org/en/stable/publish/gh-pages.html

and specifically this command from within the ```main``` branch:

```
ghp-import -n -p -f _build/html
```

## Translating from the PmagPy Cookbook

We are in the process of translating the content from the PmagPy Cookbook to this updated format. 

This involves getting the .txt documents into MyST markdown. Here is what I did for a two step process that worked on the osx_developer.tex file.

```
pandoc -s osx_developer.tex -o osx_developer.rst
```

```
rst2myst convert osx_developer.rst
```
