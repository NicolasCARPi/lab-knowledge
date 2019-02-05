# Image analysis with Python

![python](python-logo.png)

## Introduction

Python is a very good choice for a lot of applications. Image analysis is one of them. It's pretty easy to get started, but it's also easy to get lost. This guide is here to help you start your project in Python.

## Foreword

This guide is opinionated. It doesn't try to show you ALL the possible ways to do something. It shows you one way that works well.

Something to know about Python: there are some incompatibilities between version 2 and version 3. Here we'll only focus on version 3 and completely ignore any Python2 code.


## Requirements

For managing libraries, we'll use Pipenv ([see this article](https://dev.to/elabftw/stop-using-sudo-pip-install-52mn)). As I said, it's just one way among others to do it, but it's the one I think is the best.

Make sure to have this installed on your computer:

* Python 3.6+
* `pip`
* [Pipenv](https://pipenv.readthedocs.io/en/latest/)

## Getting started

Create a project:

~~~bash
cd $dev
mkdir my-python-project
cd my-python-project
git init
~~~

This is the only time I'll mention `git` in this howto. If you are not using it yet, stop what you are doing and get educated about it. Doing anything related to programming without using `git` (or another VCS) is very bad. Learn `git` basics.


Now we have an empty folder. Let's talk about which libraries we might want to use in our project. Let's make the assumption that our project involves reading TIFF files and measuring pixel intensities in these images, with some object detection, and we want to produce graphs (scatter plots, histograms, …).

## Libraries for image analysis

Python has 167,184 available libraries at the time of writing (on [Pypi.org](https://pypi.org/)). It can be hard to know which one to use. This is why I started writing this guide. Because we don't want to pollute our system with libraries for our project, we'll use [Pipenv](https://pipenv.readthedocs.io/en/latest/) to manage them **per project**. This also allows us to freeze libraries to a particular version, so you don't have surprises after an update or if you run the software on another computer with different versions installed.

### Numpy

[Numpy](http://www.numpy.org/) is the basic block of any self-respecting python software. It brings you multidimensional arrays (something lacking in python's standard library) and a bunch of other nice things. A lot of other libraries interact directly with numpy arrays. It really is _the fundamental package for scientific computing with Python_ as they claim on their webpage.

Install it with:

~~~bash
pipenv install numpy
~~~

Open your program (`my-program.py`) with your favorite editor and import it:

~~~py
import numpy as np
~~~

We import it as "np" to save keystrokes. It's also pretty standard to import it like this.

Try it out:

~~~bash
pipenv run python
>>> import numpy as np
>>> np.pi
>>> a = np.array([1, 3, 5, 12, 1329, 1245])
>>> a.shape
>>> a.dtype
~~~

Check out [this tutorial](https://docs.scipy.org/doc/numpy/user/quickstart.html) to know more about Numpy.

### Matplotlib

[Matplotlib](https://matplotlib.org/) is the _de facto_ standard for producing graphs. Have a look at their [gallery](https://matplotlib.org/gallery/index.html) it can do pretty much everything you can think of (and more!).

This is what we're gonna use for our project. Check out the [tutorials](https://matplotlib.org/tutorials/index.html) to see how it works.

~~~bash
pipenv install matplotlib
~~~

~~~py
import matplotlib.pyplot as plt
~~~

Again, we are importing it as an alias to save keystrokes. It's also quite common to import it like this.

Note: [Seaborn](https://seaborn.pydata.org/) is a good visualization library that can be very useful to get an idea of what your data looks like. But it is not designed for calculating things (see [this issue](https://github.com/mwaskom/seaborn/issues/207)).

### Image processing libraries

[Mahotas](https://mahotas.readthedocs.io/) can be used for thresholding, object detection and labelling among other things.
[Scikit-image](https://scikit-image.org/) might be more complete. See the [gallery](http://scikit-image.org/docs/stable/auto_examples/).

I have found that `skimage` was good with multidimensional TIFF images, so that's what I use.

~~~bash
pipenv install mahotas skimage
~~~

~~~py
import mahotas as mh
import skimage.io
img = skimage.io.imread('path/to/raw.tif')
~~~

### Pandas

[Pandas](https://pandas.pydata.org/) is a data analysis library. You can think of it like Excel. You load your data in a dataframe and process it any way you want. It is very powerful and you definitely want to get familiar with it.

~~~bash
pipenv install pandas
~~~

~~~py
import pandas as pd
~~~

Again, we are importing it as an alias to save keystrokes. It's also quite common to import it like this.

[This tutorial](https://www.datacamp.com/community/tutorials/pandas-tutorial-dataframe-python) might be more accessible than the official documentation that is a bit thick ;).

## Wrapping up

Our little project could do like this:

* load raw data (scikit-image)
* process it (extract quantitative data) (mahotas, numpy and friends)
* store said data in a dataframe (pandas)
* make figures (matplotlib)
* process the data (make stats) (pandas and friends)
* export as .csv/.xlsx (pandas and friends)

Of course Stack Overflow is your friend! ;)

## Things to have in your environment

* Use a real IDE for editing code, so you have autocompletion, function signatures and more
* Follow [PEP-8](https://www.python.org/dev/peps/pep-0008/) standard
* Use a [linter](https://www.pylint.org/) to check code as you write

## Going further

* Add type hinting and check it with [mypy](http://www.mypy-lang.org/)
* Make a modular project, create a proper package
* Create a docker image with your project
* Add a GUI
* Create a .exe with [Nuitka](http://nuitka.net/) so windows noobs can run it easily

Have fun!
