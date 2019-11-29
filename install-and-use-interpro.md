# Using InterProScan as a protein classification tool

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

* Java JDK/JRE version 11
* Perl 5
* Python 3 

 > __optional:__ For conda user, Java is need to be installed seperately by simply download through bioconda channel [![java](https://img.shields.io/badge/install-java-orange)](https://anaconda.org/conda-forge/openjdk)

```sh
# create environment name 'iprscan' and install openjdk
conda create -n iprscan openjdk
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

# checksum (if the downloaded file complete, this command must return 'interproscan-5.39-77.0-64-bit.tar.gz: OK')
md5sum -c interproscan-5.39-77.0-64-bit.tar.gz.md5

```

 > __Optional:__ We have a copy of the installer and Panther model database in our lab. The installer is available on Private FTP of our lab for users in Prince of Songkhla University. Use this command below to download and checksum

```sh
# download installer pack and checksum file
wget ftp://172.28.31.82/interproscan-v5.39/interproscan-5.39-77.0.tar.gz
wget ftp://172.28.31.82/interproscan-v5.39/interproscan-5.39-77.0.tar.gz.md5

# checksum
md5sum -c interproscan-5.39-77.0.tar.gz.md5

```

