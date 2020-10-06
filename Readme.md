<table>
   <tr>
       <td>
       <div align="left">
         <img src="images/savu_logo.png" width="450"><br>
       </div>
       </td>
       <td>
       <font size="5"><b> <a href="https://arxiv.org/pdf/1610.08015">Tomography Reconstruction and Processing Pipeline</a></b></font>
       <br><font size="3" face="verdana" color="green"><b> Savu</b> is a Python package to assist with the processing and reconstruction of N-dimensional parallel-beam tomography data. The project originated in the Data Analysis Group at the Diamond Light Source (UK synchrotron) to address the growing, and increasingly complex, needs of the tomography community.
       </font></br>
       <br>
       <b>Savu-lite is designed to run on a local workstation without access to the HPC resources. The overall functionality of Savu is preserved with Savu-lite. </b>
       </br>
       </td>
   </tr>
</table>

## Software highlights of Savu-lite:
* A variety of data loaders optimised for NeXus/HDF5 data format
* Savu uses parallel HDF5 files that act like numpy arrays and therefore reduces dependence on RAM
* Easy access to various software such as Astra-toolbox, TomoPy, TIGRE, ToMoBAR and others
* Quick access to more than a hundred of various plugins for data processing, reconstruction and analysis

==================================================================
## Different ways to install Savu-lite on a Unix-based workstation:

### Installation of a pre-built Savu-lite package into a _clean_ [conda](https://conda.io/projects/conda/en/latest/user-guide/install/index.html) environment
```
conda install -c savu-dep savu-lite
```

### Installation of Savu-lite package using created environment file:
 - Install **Miniconda3** and activate base environment
 - Modify `PREFIX` in `recipe/envs/environment_fixed.yml` to your desired installation location
 - `conda env create -f recipe/envs/environment_fixed.yml`
 - `conda activate savu3-lite`
 - Go to the main [Savu](https://github.com/DiamondLightSource/Savu/) folder and execute `python setup.py install` and that'll install **Savu** in your environment

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
