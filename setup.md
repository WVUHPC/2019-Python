---
title: Setup
---

If you are using your personal computer instead of the cluster, there are several pieces of software you will wish to install before the workshop.
Though installation help will be provided at the workshop,
we recommend that these tools are installed (or at least downloaded) beforehand.
For example, Anaconda Python is a very large download.

## Python 3

You need an implementation of Python 3. There are several ways you can achieve that. You can use the Official CPython version from <https://www.python.org/downloads/> and after install the scientific packages with pip. In particular, we will use Numpy, Scipy, Matplotlib, Pandas and Cython. With those packages you have a fairly decent environment to start doing scientific computing on Python.

Another option is the Intel Distribution of Python <https://software.intel.com/en-us/distribution-for-python>. It includes optimized versions of Numpy, Scipy and scikit-learn that uses the optimized MKL on background. In term of performance this is a better choice over the Official Python distribution and packages from pip.

Another option is installing Miniconda or Anaconda from [https://www.continuum.io/downloads](https://www.continuum.io/downloads).
Anaconda is a free version of Python that comes bundled with all of its most useful tools.

## SSH Client

If you plan to work from the cluster you should have an SSH client installed.
SSH is a tool that allows us to connect to and use a remote computer as our own.
Please follow the directions below to install an SSH client for your system.

**Windows**

Install MobaXterm from [http://mobaxterm.mobatek.net](http://mobaxterm.mobatek.net).
You will want to get the Home edition (Installer edition).

**macOS**

Although macOS comes with SSH pre-installed,
you will typically want to install [XQuartz](www.xquartz.org) to enable graphical support.
Note that you must restart your computer to complete the installation.

**Linux**

Linux users do not need to install anything, you should be set!

{% include links.md %}
