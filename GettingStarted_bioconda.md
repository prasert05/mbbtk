# Getting started with Bioconda and Bioconda
In our lab, We prefer to use Miniconda3 to manage environment for such a software with a specific version of its dependencies by isolate them into a specific environments. Moreover, we usually perform computational analyses on shared server of our department, so managing environment with miniconda make user to perform any software without root permission and user can manage environment, such as add recipes (any packages in bioconda), create environment, or even delete environment by themselves.

Prior to use Bioconda, the Miniconda3 package is required to install on your local machine. We briefly summarized how to install Bioconda from [Bioconda's user docs](https://bioconda.github.io/user/install.html) as a reference for installation.

> __Note:__ Even miniconda is suitable for Windows OS, but many recipes in Bioconda does not support Windows. So, we would prefer to use on Linux OS

__Prerequisites:__ Personal laptop or Server with Linux 64-bit operation system.

## 1. Install miniconda
> Python 3 version is preferred to install Miniconda3. 

```sh
# download Miniconda3 from Anaconda repository
$ wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh

# execute the downloaded package
$ bash Miniconda3-latest-Linux-x86_64.sh
```
During install the Miniconda, follow the End-User License Agreement (EULA) and its instruction. 

 :warning: :warning: __While the installation is completed, restart the terminal.__ :warning: :warning:

## 2. Set up channels to bioconda
By default, the main channel of miniconda to download the recipes is `conda-forge`. According to the reerence, The conda-forge channel contains many general-purpose packages not already found in the `defaults` channel. Setting the `Bioconda` channel to the first prioroty is required for bioinformatics research.

```sh
$ conda config --add channels defaults
$ conda config --add channels bioconda
$ conda config --add channels conda-forge
```

## 3. Manage environment (optional)

This content is referred from [Conda's managing environment docs](https://docs.conda.io/projects/conda/en/latest/user-guide/tasks/manage-environments.html). User can create, export, list, remove, and update environments as you prefer. Or even backup and share the environment via `.yml` metafile.

The `base` is the default environment when the installation is completed. But if you don't want `base` to activativate automatically, simply type:
```sh
$ conda config --set auto_activate_base false
```
### Creating an environment via terminal:
```sh
# Create environment named 'myenv'
$ conda create --name myenv

# activate 'myenv' environment
$ conda activate myenv

# deactivate 'myenv' environment
$ conda deactivate myenv
```
When conda asks you to proceed, type `y`, or you can integrate `-y` parameter in the upper command to let the conda know that I accept all change.

After create environment is finished, it will keep the metafile in `~/miniconda3/envs/`

### Create an environment with a specific version of Python:
```sh
# Create 'myenv' environment with a specific python 3.7 version
$ conda create -n myenv python=3.7
```
### Create an environment with a specific package:
```sh
# Install 'scipy' recipe within 'myenv' environment
$ conda create -n myenv scipy
```

### Create environment with a specific version of python and version of recipe:

```sh
# create 'deepsig' environment with python 2.7 version, 'biopython' recipe version 1.72, 'tensorflow' recipe version 1.5.0 and 'keras' recipe version 2.2.4
$ conda create -n deepsig python=2.7 biopython=1.72 tensorflow=1.5.0 keras=2.2.4
```
### Export environment as `.yml` file
```sh
# export current environment into environment.yml
$ conda env export > environment.yml
```

### Creating an environment from an environment.yml file:
```sh
# create and import environment from environment.yml
$ conda env create -f environment.yml
```

### Check list of environment you've created:
```sh
# check environment list
$ conda env list
```
Example result:
> Note: The `*` shows the current environment
```
(base) jiratchaya@PowerEdge-R440:~/rawdata$ conda env list
# conda environments:
#
base                  *  /home/jiratchaya/miniconda3
cutadapt                 /home/jiratchaya/miniconda3/envs/cutadapt
deepsig                  /home/jiratchaya/miniconda3/envs/deepsig
fastp                    /home/jiratchaya/miniconda3/envs/fastp  
phobius                  /home/jiratchaya/miniconda3/envs/phobius
trinity                  /home/jiratchaya/miniconda3/envs/trinity
```
### Removing an environment:
```sh
$ conda remove --name myenv --all
```
## 4. Install bioconda recipes
You can browse available bioconda recipes from [![Recipe index](https://img.shields.io/static/v1?label=Recipe&message=index&color=blue)](https://bioconda.github.io/conda-recipe_index.html)

to install bioconda recipe, simply type:
```sh
$ conda install trinity
```
When bioconda asks you to proceed, type `y`, or you can integrate `-y` parameter in the upper command to let the bioconda know that I accept all change.