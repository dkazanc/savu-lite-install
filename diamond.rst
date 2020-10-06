===================================
Diamond Light Source Specific Notes
===================================

Use local machine whenever possible
-----------------------------------

Anything run on the main network is very slow, local machine is much faster.

**Temporary Path**

TMPPATH needs to be set to local machine otherwise build process takes five times as long!
Create a “.bashrx_local” file containing the following line:

  ``export   TMPPATH=/scratch/temporary-folder-name``

Even with this, still need to check /tmp for accumulation of system detritus that can leave environment with insufficient available space to perform a Conda build. 

**Don’t use Environment Module version of Conda**

Using modules network version is slow when run on network and has permissions problems when using it locally on /scratch.
Recommend downloading and installing miniconda on scratch.

I suspect that Conda does not react well with alternative installation and environmental control mechanisms such as Module Load and Pip, particularly when attempting to resolve dependency conflicts.

*Testing savu-lite on Environment Module Python/2.7 on network*

Very slow and failed on multiple dependency issues.  Concluding note
“Note that strict channel priority may have removed packages required for satisfiability.”
may indicate it further investigation with more flexible channel handling may help; not convinced it is worth the time though.

**Beware Environmental Errors**

Check /tmp for accumulation of system detritus that can leave environment with insufficient available space to perform a Conda build. Errors due to this are not always easy to distinguish from actual build errors.




