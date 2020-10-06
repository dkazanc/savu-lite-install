=======
Testing
=======

.. _trainingexamples: https://savu.readthedocs.io/en/latest/user_guides/user_training/#training-examples

Test Environment
----------------

To create a test environment (called "test" in command below)

  ``conda create --name test python=2``

To switch to "test" environment:

  ``conda activate test``

To reset "test" environment to initial install:

  ``conda install --name test --revision 0``

Savu Training Examples
----------------------

Training examples are documented here: `trainingexamples`_

**Simple**

This can be run if in the TrainingExample root directory as follows:

  ``savu data/24737.nxs process_lists/simple_tomo_pipeline_cpu.nxs .``

Data files have to be opened and saved by savu_config to avoid import error for a module nxtomo_loader; pending a future formal fix to Savu.

**Parallel**

This can be run if in the TrainingExample root directory as follows assuming a writeable "/tmp2" folder exists:

  ``savu_mpijob_local.sh data/24737.nxs process_lists/simple_tomo_pipeline.nxs . -d /tmp2``

This currently fails, but is not a priority as savu-lite was not intended to run in parallel.

Current Error is:

  Global Name ‘mpi4py’ is not defined

Existing Savu Tests
-------------------

These can be run successfully from a conda installed savu-lite.

* savu_quick_tests
* savu_full_test

**savu_quick_tests**

This is run as part of the build. scikit-image is a pre-requisite for it to run and has therefore been included in savu-lite build.

**savu_full_test**

This can be run after savu-lite has been installed, success is indicated by it completing with no errors reported at its conclusion.
Pre-requisites for this to run are: tifffile, pyfai, peakutils, fabio, tomopy, pymca

  https://pypi.org/project/pynvml/#description

  https://github.com/vasole/pymca/blob/master/PyMca5/PyMcaPhysics/xrf/FastXRFLinearFit.py

Savu Issues
-----------

Refresh.py is awaiting a fix that will be introduced in next release.

**Training Example Errors**

The Savu 2.4 training examples are out-of-date: `trainingexamples`_

Refresh.py is awaiting a fix that will be introduced in next release.
python process_lists/refresh.py

In the meantime this can be resolved by opening data files with savu_config and then re-saving them. Thus avoiding import error for a module nxtomo_loader.


