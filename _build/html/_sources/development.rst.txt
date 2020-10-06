===========
Development
===========

.. _trainingexamples: https://savu.readthedocs.io/en/latest/user_guides/user_training/#training-examples
.. _sphinxguide: https://www.sphinx-doc.org/en/master/usage/quickstart.html
.. _savudocs: https://readthedocs.org/projects/savu/
.. _condaguide: https://towardsdatascience.com/a-guide-to-conda-environments-bc6180fc533
.. _readthedocsguide: https://docs.readthedocs.io/en/stable/
.. _pandoc: https://pandoc.org/

Development notes for savu-lite

Cooking with Conda
==================

To set-up the basic development environment download Miniconda2-latest-linux-x86_64.sh and install on local machine.  Update to get latest versions and then install conda-build,  conda-verify, sphinx (for documentation), and anaconda-client (to allow uploading to anaconda cloud).

1) ``conda update conda``
2) ``conda install conda-build``
3) ``conda install conda-verify``
4) ``conda install sphinx``
5) ``conda install anaconda-client``


Building savu-lite
==================

Build Sequence
--------------

Move to python 2 environment "miniconda2"

  ``conda activate miniconda2``

From directory containing meta.yaml and build.sh {the only required files}

  ``conda-build purge``
  ``conda-build .``

Upload resulting file that will be created in linux-64 folder {first time it will create anaconda-project.yml}

  ``anaconda upload linux-64/savu.....``

Test by downloading file from test channel into fresh test environment

  ``conda install -c test_channel savu-lite``

Run training example and savu_full_test

Upload to savu-dep if testing passes

  ``anaconda upload -u savu-dep linux-64/savu.....``

Channels
--------

**Default channels used**

* https://repo.anaconda.com/pkgs/main/linux-64
* https://repo.anaconda.com/pkgs/main/noarch
* https://repo.anaconda.com/pkgs/r/linux-64
* https://repo.anaconda.com/pkgs/r/noarch
* https://conda.anaconda.org/conda-forge/linux-64
* https://conda.anaconda.org/conda-forge/noarch

**Additional channels used**

* https://conda.anaconda.org/astra-toolbox/label/dev/linux-64
* https://conda.anaconda.org/astra-toolbox/label/dev/noarch
* https://conda.anaconda.org/ccpi/linux-64
* https://conda.anaconda.org/ccpi/noarch
* https://conda.anaconda.org/dkazanc/linux-64
* https://conda.anaconda.org/dkazanc/noarch

**Channel Priority**

Channel_Priority is one of strict, flexible, disabled.  Strict chosen as it should be quickest as it takes stops when it finds a package looking in defined order.

*.condarc includes*

* channels:

  * defaults
  * conda-forge
  * astra-toolbox/label/dev
  * ccpi
  * dkazanc

* auto_activate_base: false
* show_channel_urls: true
* unsatisfiable_hints: true

**Local Channels Creation**

Created a Conda Environment and install conda-build

  ``conda create --name local_channel_name python=2 conda-build``

  ``conda install conda-build``

To create a local channel for python package "click":

  ``conda skeleton pypi click``

  ``conda-build click``

*whenever local channels change*
run the following in the channel root directory:

  ``conda index``

Able to pick-up local version of click using:

  ``conda install -c local_channel_name click``

Use of PIP with conda
---------------------

pip installs are not recommended as they mix poorly Conda and should be done after conda installs completed!?

Currently the following files need to be pip installed as part of the build.sh script:

* gnureadline (8.0.0) - deprecated and no longer recommended for use
* nvidia-ml-py (7.352.0) - older python 2 version

However Conda and Pip don’t play well together and this is only an interim solution.

**Gnureadline**

This is reasonably low-risk given the lack of dependencies. The long-term solution is likely to be removal of dependency in Savu.
Conda install options listed at: https://anaconda.org/conda-forge/gnureadline do not work.

**Nvidia-ml-py**

https://files.pythonhosted.org/packages/72/31/378ca145e919ca415641a0f17f2669fa98c482a81f1f8fdfb72b1f9dbb37/nvidia-ml-py-7.352.0.tar.gz

Anaconda Cloud
--------------

Anaconda Cloud is best delivery mechanism for savu-lite.  Adding the built package to existing savu-dep anaconda cloud repository automatically allows conda install with savu-dep as the channel.  This seems much easier that attempting to set-up a continuous integration build on conda-forge that would not be of much use for this application.  It also quick, less than 15 minutes to upload and requires no approval from any external entity.

**To access Anaconda Cloud**

Sign-up at: https://anaconda.org/
Add to conda installation anaconda-client as follows:

  ``conda install anaconda-client``

**Notes**
needed to delete and re-add to change documentation URL shown on Anaconda Cloud.

Build with Miniconda 3 or 2 ?
-----------------------------

Miniconda2 seemed to have stability issues {some packages no longer supported?!}. Miniconda3 may cause issues when used even though building a python 2 system although this needs to be reconfirmed.

Miscellaneous
-------------

**Python 2 “end of life”**

  Any Python 2 solution will be frozen in time as support for dependant libraries will diminish and cease.
  Currently 2.7.16 used, 2.7.17 is latest with 2.7.18 due in April

  numpy is no longer supported for python 2; last available version that can be used is 1.16.6

**Virtual Packages**
exist for: cuda (__cuda) and glibc (__glibc)
These can detect presence of and return version numbers for features that cannot be managed directly by conda.

**yaml**
need pyyaml in recipe to import yaml even though yaml is installed

**pandoc**

A very nice tool that automatically converts between document formats, it is available via conda, and should do most and in simple cases all of the necessary work for likely source formats. As a command line tools it is automation friendly. Details can be found at `pandoc`_

Useful Links
============

* Guide to Conda environments - `condaguide`_
* ReadtheDocs Guide - `readthedocsguide`_ (incorporates a good “Getting Started with Sphinx”)
* Existing ReadtheDocs Project account - `savudocs`_
* Sphinx Quick Start Guide - `sphinxguide`_
* pandoc file conversion tool - `pandoc`_


