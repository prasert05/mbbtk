# Using InterProScan based on Bioconda

[InterProScan intro](https://github.com/ebi-pf-team/interproscan/wiki#what-is-interproscan)

## Prerequisites
* Personal computer or server with 64-bit GNU/Linux operating system
	> To check the Linux system information, simply type command below in the terminal.

```sh
uname -a
# The expected output sequentially should be your kernel name, localhost name, kernel release, 
# kernel version, machine hardware name (ex. x86_64 or x86_32), 
# processor type (ex. x86_64 or x86_32), hardware platform (ex. x86_64 or x86_32) 
# and operating system name
```
* Bioconda
* Java JDK/JRE version 11
* Perl 5
* Python 3 

 > __optional:__ 
 > For conda user, For conda user, Java is need to be installed seperately by simply download through conda-forge channel [![java](https://img.shields.io/badge/install-java-orange)](https://anaconda.org/conda-forge/openjdk). Simply do as follow:
```sh
# Create environment for InterProScan's dependencies
conda create -n iprscan

# Activate channel
conda activate iprscan

# Install Java openJDK
conda install -c conda-forge python=3.8.1 openjdk=11.0.1

```

## Download InterProScan installer and extensions

### InterProScan installer

InterProScan installer can be downloaded from ftp://ftp.ebi.ac.uk/pub/software/unix/iprscan/5. InterProScan lastest version we've used is v5.39 (ftp://ftp.ebi.ac.uk/pub/software/unix/iprscan/5/5.39-77.0/interproscan-5.39-77.0-64-bit.tar.gz). According to the recommendation of [ebi-pf-team](https://github.com/ebi-pf-team/interproscan/wiki/HowToDownload#64-bit-distribution). MD5 cheksum is mandatory for a large downloaded file. So the command below is to create directory, download the installer and checksum.

```sh

# create directory name 'iprscan' and enter to the directory
mkdir iprscan && cd iprscan

# download installer and checksum file
wget ftp://ftp.ebi.ac.uk/pub/software/unix/iprscan/5/5.39-77.0/interproscan-5.39-77.0-64-bit.tar.gz
wget ftp://ftp.ebi.ac.uk/pub/software/unix/iprscan/5/5.39-77.0/interproscan-5.39-77.0-64-bit.tar.gz.md5

# checksum (if the downloaded file complete, this must return 'interproscan-5.39-77.0-64-bit.tar.gz: OK')
md5sum -c interproscan-5.39-77.0-64-bit.tar.gz.md5

# decompress file
tar zxvpf interproscan-5.39-77.0-64-bit.tar.gz

```

After extracted file installer, it is optional to doownload the Panther model.

### Install Panther model extension


 > __Optional:__ We have a copy of the installer and Panther model database in our lab. The installer is available on Private FTP of our lab for users in Prince of Songkhla University. Use this command below to download and checksum

```sh
# download installer pack and md5 file
wget ftp://172.28.31.82/interproscan-v5.39/interproscan-5.39-77.0.tar.gz
wget ftp://172.28.31.82/interproscan-v5.39/interproscan-5.39-77.0.tar.gz.md5

# checksum
md5sum -c interproscan-5.39-77.0.tar.gz.md5

```

Panther is a protein classification system through evolutionary relationship. Panther classify proteins  into hierarchy according to: 
	- __Family and subfamily:__ families are groups of evolutionarily related proteins; subfamilies are related proteins that also have the same function
	- __Molecular function:__ the function of the protein by itself or with directly interacting proteins at a biochemical level, e.g. a protein kinase
	- __Biological process:__ the function of the protein in the context of a larger network of proteins that interact to accomplish a process at the level of the cell or organism, e.g. mitosis.
	- __Pathway:__ similar to biological process, but a pathway also explicitly specifies the relationships between the interacting molecules.

For more information, please find out more via [Panther website](http://www.pantherdb.org/about.jsp).

download Panther model:

```sh
# go to 'data' subdirectory within 'interproscan-5.39-77.0' directory
cd interproscan-5.39-77.0/data

# download formatted Panther model and md5 file
wget ftp://ftp.ebi.ac.uk/pub/software/unix/iprscan/5/data/panther-data-14.1.tar.gz
wget ftp://ftp.ebi.ac.uk/pub/software/unix/iprscan/5/data/panther-data-14.1.tar.gz.md5

# cheksum (if the downloaded file complete, this must return 'panther-data-14.1.tar.gz: OK', if not try to download again)
md5sum -c panther-data-14.1.tar.gz.md5

# decompress file
tar zxvpf panther-data-14.1.tar.gz

```

## Run InterProScan

To run InterProScan, simply type

```sh
./interproscan.sh
```

> Note: Make sure that your current working directory is 'interproscan-5.39-77.0/' that all scripts contains in. 

For command description, please see [How to run InterProScan](https://github.com/ebi-pf-team/interproscan/wiki/HowToDownload#64-bit-distribution) on [ebi-pf-team](https://github.com/ebi-pf-team)'s GitHub.