---
nav_order: 2
layout: page
title: Installation
---

# Installing BARAM for Windows
Binary installation package for 64bit windows is prepared for convenience.  
Download it from following link.

[Download BARAM v22.0.6 Installer for 64 bit Windows ›](http://d3c6e16xufx1gb.cloudfront.net/BARAM-22.0.6-setup.exe){: .btn .btn-purple .text-center .fs-5}

# Installing BARAM from Source Code

## Supported Platforms
* Windows 10 or newer
* macOS 10.14 or newer
* Ubuntu 20.04 or newer
* CentOS 8.2 or newer ( Rocky Linux, AlmaLinux, ... )
* OpenSUSE Leap 15.4
* Linux Mint 21 "Vanessa"

## BARAM requires following installed software:

* Python 3.9 or newer
* [MS-MPI](https://docs.microsoft.com/en-us/message-passing-interface/microsoft-mpi) 10.0 or newer ( Windows Only )
* OpenMPI 4.0 or newer ( Linux, macOS )
* GNU C Compiler or any other C Compiler ( Linux, macOS )

## Clone the source code
```commandline
git clone https://github.com/nextfoam/baram.git
```

## Setup Python virtual environment

Run following command in the top directory of downloaded source code.
Please don't forget that Python **3.9.x** is required.
You can check it with the command of `python3 -V`.

```commandline
python3.9 -m venv venv
```

## Enter into virtual environment
Run following command in the top directory of downloaded source code

### On Windows
```commandline
.\venv\Scripts\activate.bat
```

### On Linux or macOS
```commandline
source ./venv/bin/activate
```

## Install Python packages
Run following command in the top directory of downloaded source code
```commandline
pip install -r requirements.txt
```

## Copy Solver Executables
Download and uncompress solver executables into the top directory of downloaded source code.
The compressed files have _**solvers**_ folder in it.
Put _**solvers**_ folder into the top directory.
The final directory structure may look like following.
```
($BARAM)
|
+-- requirements.txt
+-- ...
+-- solvers/
|   |
|   +-- openfoam/
|       |
|       +-- bin/
|       +-- etc/
|       +-- ...
+-- ...
```

### Windows
[solvers_windows_20221124.zip](http://d3c6e16xufx1gb.cloudfront.net/solvers_windows_20221124.zip)


### Linux
[solvers_linux_20221117.tar.xz](http://d3c6e16xufx1gb.cloudfront.net/solvers_linux_20221117.tar.xz)

You can download the file on command line with cURL or wget command like following.

```commandline
wget http://d3c6e16xufx1gb.cloudfront.net/solvers_linux_20221117.tar.xz
```

```commandline
curl -L http://d3c6e16xufx1gb.cloudfront.net/solvers_linux_20221117.tar.xz -o solvers_linux_20221117.tar.xz
```

### macOS
[solvers_mac_20220908.tar.gz](http://d3c6e16xufx1gb.cloudfront.net/solvers_mac_20220908.tar.gz)


## Compile Daemonizer ( only for Linux and macOS )
"solvers" directory was created when the compressed file was uncompressed.
```commandline
gcc -o solvers/openfoam/bin/baramd misc/baramd.c
```

## Compile Resource Files
```commandline
python convertUi.py
```

## Run BARAM
```commandline
python main.py
```

