# Using InterProScan as a protein classification tool

[InterProScan intro](https://github.com/ebi-pf-team/interproscan/wiki#what-is-interproscan)

## Prerequisites
* Personal computer or server with 64-bit GNU/Linux operating system
	> To check the Linux system information, simply type command below in the terminal.

	```
	$ uname -a
	# The expected output sequentially should be your kernel name, localhost name, kernel release, 
	# kernel version, machine hardware name (ex. x86_64 or x86_32), 
	# processor type (ex. x86_64 or x86_32), hardware platform (ex. x86_64 or x86_32) 
	# and operating system name
	```

* Java JDK/JRE version 11
* Perl 5
* Python 3

__optional:__ Perl 5 and Python 3 are already installed in miniconda platform. Java is need to be installed seperately by simply download through bioconda channel:

```
$ conda install -c bioconda java-jdk
```
