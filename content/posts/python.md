---
title: "Python"
date: 2022-02-17T11:43:06+01:00
tags: ['python']
draft: false
---

The [python-guide](https://docs.python-guide.org/) provides a similar list, but
goes into much more detail.
On this page I will limit myself to my personal preferences, and give some
links to documentation.

# Install

Python is installed by default in all linux distributions.  Python2 is not
recommended: when it is available on your system, it is mostly to support legacy
applications.  Python3 is the way to go for any new code.

## Packages

Popular python packages are available in your linux distribution, but many more
are on the [Python Package Index](https://pypi.org/).
Those can be installed using ```pip```:
```bash
pip install $PACKAGE_NAME
```

You can install a list of packages automatically using ```-r```:
```bash
pip install -r requirements.txt
```
where ```requirements.txt``` is the conventional file name.


By default, ```pip``` will install packages globally (or in your user account).
Especially if you are developping, it is a good practice to setup a virtual
environment so you do not interfere with the system packages.


To install packages directly from Github (useful when not released on PyPi):
```bash
python -m pip install SomeProject@git+https://git.repo/some_pkg.git@1.3.1
```
More information can be found [in the PyPi documentation](https://pip.pypa.io/en/stable/cli/pip_install/).


## Virtual environment

A virtual environment is a way to keep software installed with ```pip``` from
interfering with your system's python.  All packages, and their dependencies,
are contained in a folder in your local file system.  On this page I call the
folder ```env```, but you can use any name.
```bash
mkdir env
python -m venv env
. env/bin/activate
```

For some dependencies, you might not want to install it locally, or you don't
need the most recent versions.  You can have ```pip``` use the globally
installed (system) version of a package, if available, by initializing your
repository as:
```bash
python -m venv env --system-site-packages
```

The environment can be quite large, and contains binary files and caches. It is
good practice to exclude this from your version controll.  For ```git```:
```bash
echo env >> .gitignore
```

Deleting the folder ```env``` will completely remove all packages and files created by ```pip```:
```bash
deactivate  # remove the env from your path (optional)
rm -rf env
```

A completely different approach to python packages is
[Anaconda](https://www.anaconda.com).  This is based on a binary-distribution
approach, look on the their website for a
[comparison](https://www.anaconda.com/blog/understanding-conda-and-pip).
You can even both: run pip from an anaconda environment.

I much prefer PyPi, and hardly have any issues. Stuff just works (Fedora linux on an intel+nvidia laptop).

## Using a specific python version

Some libraries require specific versions of python.  An annoying example is
PyTorch, which doesn't work with a too new python.  A common workaround is to
install a lower version of python using your systems package manager, and
specify your interpreter when initializing your environment:
```bash
virtualenv -p $CUSTOM_PYTHON_INTERPRETER env
```

# Write code

## Project layout

Keeping your code, documentation, and test nicely organized is crucial when
writing a larger program, or when working with multiple people on a code.
There are plenty of tutorials; I like the [python-guide](https://docs.python-guide.org/writing/structure/).
Also interesting is [this discussion](https://caremad.io/posts/2013/07/setup-vs-requirement/) on
what to put in ```requirements.txt``` and what in ```setup.cfg```.
```
git_root_folder/
├── LICENSE
├── README.md
├── Makefile
├── docs/
├── .gitignore
├── pyproject.toml
├── requirements.txt
├── setup.cfg
├── src/
│   └── example_package/
│       ├── __init__.py
│       └── example.py
└── tests/
```

## Highlighting

Vim provides syntax highlighting for python by default.

## Linting

Vim, via the [ALE](https://github.com/dense-analysis/ale) plugin, provides many
linting and code quality plugins; you can see which linters are available using
```:ALEInfo``` in Vim.  I'm using ```flake8```, ```mypy```, and ```pylint```.

## Language server

A maintained language server is available [here](https://github.com/python-lsp/python-lsp-server).
Install using ```pip```:
```bash
pip install python-lsp-server
```

## Logging

Use pythons default [logging framework](https://docs.python.org/3/library/logging.html).
```python3
import logging

# do this in __main__
logging.basicConfig(level=logging.INFO)

# do this in each module separately
logger = logging.getLogger(__name__)
logger.info('message')
```

## Debugging

Add breakpoints to you code (Python 3.7 and later):
```python
breakpoint()
```
or run your program under ```pdb```:
```bash
python -m pdb $PROGRAM $PROGRAM_ARGS
```
For documentation see this [Real Python](https://realpython.com/python-debugging-pdb/) page.

I haven't used this much, but you can also debug directly from Vim.
 * For a solution based on Vim's ```:terminal``` mode see [vim-repl](https://github.com/sillybun/vim-repl)
 * For a generic solution using the Debug Adapter Protocol take a look at 
   [vimspector](https://github.com/puremourning/vimspector)

## Testing

Python3 comes with a default testing framework
[unittest](https://docs.python.org/3/library/unittest.html#module-unittest).

```bash
python -m unittest $WHAT_TO_TEST
```
where you can test modules, a class or a method, or a filename.
When run without arguments, ```unittest``` will do its own test discovery.

Alternatively, [PyTest](https://docs.pytest.org) is also popular.

## Profiling

Easy profiling with [cProfile](https://docs.python.org/3/library/profile.html).
Pass your program as an argument to the ```cProfile``` module:
```bash
python -m cProfile [-o output_file] [-s sort_order] (-m module | myscript.py)
```

## Packaging

Python has an extensive guide on [packaging your project](https://packaging.python.org/en/latest/tutorials/packaging-projects/).
It requires a (sensible) project layout, so it makes sense to read that section before
starting a big project.

# Interactive use

## Notebooks 

Jupyter

## REPL

IPython, bpython, ptpython

# Recommended packages

