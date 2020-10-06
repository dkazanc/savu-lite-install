=========================
Installation of savu-lite
=========================

.. _conda-install: https://conda.io/projects/conda/en/latest/user-guide/install/index.html

Installing savu-lite requires a minimal miniconda environment be installed first.

**Install Miniconda**
by downloading Miniconda2-latest-linux-x86_64.sh and install on local machine `conda-install`_

**Update Miniconda**
to latest package versions:

  ``conda update conda``

**Install savu-lite**
into the base conda environment:

  ``conda install -c savu-dep savu-lite``

Optional Additions
------------------

*tomopy* is not required to run the basic training example of savu tests, but may be required for any further experimentation.

  ``conda install tomopy``

