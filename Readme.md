<table>
   <tr>
       <td>
       <div align="left">
         <img src="images/savu_logo.png" width="450"><br>
       </div>
       </td>
       <td>
       <font size="5"><b> Tomography Reconstruction and Processing Pipeline</b></font>
       <br><font size="3" face="verdana" color="green"><b> <a href="https://github.com/DiamondLightSource/Savu/">Savu</a></b> is a Python package to assist with the processing and reconstruction of N-dimensional parallel-beam tomography data (see the <a href="https://arxiv.org/pdf/1610.08015">paper</a>). The project originated in the Data Analysis Group at the Diamond Light Source (UK synchrotron) to address the growing, and increasingly complex, needs of the tomography community.
       </font></br>
       <br>
       <b>Savu-lite is designed to run on a local workstation without access to the HPC resources. The main functionality of Savu is preserved with Savu-lite. </b>
       </br>
       </td>
   </tr>
</table>

## Some highlights of Savu-lite:
* A variety of data loaders optimised for NeXus/HDF5 data format
* Savu uses parallel HDF5 files that act like numpy arrays and therefore reduces dependence on RAM
* Easy access to various software such as Astra-toolbox, TomoPy, TIGRE, ToMoBAR and others
* Quick access to more than a hundred of various plugins for data processing, reconstruction and analysis

==============================================================================
## Different ways to install Savu-lite on a Unix-based workstation:

### Installation of a pre-built Savu-lite package into a _clean_ [conda](https://conda.io/projects/conda/en/latest/user-guide/install/index.html) environment
```
conda install -c savu-dep savu-lite
```

### Installation of Savu-lite package using created environment file:
 - Install **Miniconda3** and activate base environment
 - `conda env create -f recipe/envs/environment_fixed.yml --prefix=/path/to/your/savu/environment`
 - Activate the environment
 - Go to cloned [Savu](https://github.com/DiamondLightSource/Savu/) folder and execute `python setup.py install` which will install **Savu** in your environment

### Installation of pre-built Savu-lite package using [conda-pack](https://conda.github.io/conda-pack/):
- Download Savu-lite archive from [Zenodo](https://zenodo.org/communities/ccpi/?page=1&size=20)
```
  mkdir -p savu3-lite
  tar -xzf savu3-lite.tar.gz -C savu3-lite
  source savu3-lite/bin/activate
```
- When finished working run `source savu3-lite/bin/deactivate`

### Building Savu-lite package with conda-build:
-- WIP
