# Image analysis with Python

![python](python-logo.png)

## Introduction

Python is a very good choice for a lot of applications. Image analysis is one of them. It's pretty easy to get started, but it's also easy to get lost. This guide is here to help you starting your project in Python.

## Foreword

This guide is opinionated. It doesn't try to show you ALL the possible ways to do something. It shows you one way that works well.

Something to know about Python: there are some incompatibilities between version 2 and version 3. Here we'll only focus on version 3 and completely ignore any Python2 code.

For managing libraries, we'll use Pipenv ([see this article](https://dev.to/elabftw/stop-using-sudo-pip-install-52mn)). As I said, it's just one way among others to do it, but it's the one I think is the best.

## Getting started

Create a project:

~~~bash
cd $dev
mkdir my-python-project
cd my-python-project
git init
~~~

This is the only time I'll mention git in this howto. If you are not using it yet, stop what you are doing and get educated about it. Doing anything related to programming without using `git` (or another VCS) is very bad. Learn `git` basics.


Now we have an empty folder. Let's talk about which libraries we might want to use in our project. Let's make the assumption that our project involves reading TIFF files and measuring pixel intensities in these images.

## Libraries for image analysis

Python has 167,184 projects at the time of writing. It can be hard to know which one to use. This is why I started writing this guide. Because we don't want to pollute our system with libraries for our project, we'll use [Pipenv](https://pipenv.readthedocs.io/en/latest/) to manage them **per project**. This also allows us to freeze libraries to a particular version, so you don't have surprises after an update or if you run the software on another computer with different versions installed.

### Numpy

[Numpy](http://www.numpy.org/) is the basic block of any self-respecting python software. It brings you multidimensional arrays (something lacking in python's standard library) and a bunch of other nice things. A lot of other libraries interact directly with numpy arrays. It really is __the fundamental package for scientific computing with Python__ as they claim on their webpage.

Install it with:

~~~bash
pipenv install numpy
~~~

Open your program and import it:

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

### Pandas

### Mahotas

### Scikit image



