---
title: Windows
parent: Installation
nav_order: 3
---

# Windows platform (tested with win7)
{: .no_toc }

1. TOC
{:toc}
---

## Install requirements

Tested on Win7 (64bit) with [cygwin](https://www.cygwin.com/) environment

1. Download and Install [cygwin](https://www.cygwin.com/)

2. Install [apt-cyg](https://github.com/transcode-open/apt-cyg).  

After you have installed cygwin, open the **cygwin-terminal** and run the following command to install apt-cyg.

```
  wget https://raw.githubusercontent.com/transcode-open/apt-cyg/master/apt-cyg
  chmod +x apt-cyg
  mv apt-cyg /usr/local/bin
```  

3. Install the required libraries using apt-cyg

```
  apt-cyg install make gcc-g++ cmake gdal libboost-devel libgdal-devel libexpat1-devel libbz2-devel zlib-devel swig python-devel
```

## Install C++ program and Python bindings

1. Download the fmm code, open the **cygwin-terminal**

```
mkdir fmm
cd fmm
git clone git@github.com:cyang-kth/fmm.git .
```

You check the path of the  `fmm` folder by typing `pwd` on the terminal.

2. Build and install fmm

On the **cygwin-terminal**, build and install the program with cmake
```
# Under the `fmm` folder
mkdir build
cd build
cmake ..
make -j8
make install
```
It will build executable files under the `build` folder, which are installed to `/usr/local/bin`:
- `ubodt_gen`: the Upper bounded origin destination table (UBODT) generator (precomputation) program
- `fmm`: the program implementing fast map matching algorithm
- `stmatch`: the program implementing STMATCH algorithm, no precomputation needed

It will also create a folder `python` under the build path, which contains library that can
be imported into Python. In order to import fmm successfully and that folder must be added to the environment variable `PYTHONPATH`.

Execute the commands below to add `fmm/build` folder to the environment variable `PATH` and the `build/python` folder to the environment variable `PYTHONPATH` (set the `/home/fmm/build` and `/home/fmm/build/python` below to the **absolute path** of the `build` and `build/python` folder, you can run `pwd` to check the absolute path of each folder):
```
    echo 'export PATH=/home/fmm/build:${PATH}' >> ~/.bash_profile
    echo 'export PYTHONPATH=/home/fmm/build/python:${PYTHONPATH}' >> ~/.bash_profile
    source ~/.bash_profile
```

## Verfication of installation

### Run command line map matching

Open a new terminal and type `fmm`, you should see the following output:
```
------------ Fast map matching (FMM) ------------
------------     Author: Can Yang    ------------
------------   Version: 2020.01.31   ------------
------------     Applicaton: fmm     ------------
A configuration file is given in the example folder
Run `fmm config.xml` or with arguments
fmm argument lists:
--ubodt (required) <string>: Ubodt file name
--network (required) <string>: Network file name
--gps (required) <string>: GPS file name
--output (required) <string>: Output file name
--network_id (optional) <string>: Network id name (id)
--source (optional) <string>: Network source name (source)
--target (optional) <string>: Network target name (target)
--gps_id (optional) <string>: GPS id name (id)
--gps_geom (optional) <string>: GPS geometry name (geom)
--candidates (optional) <int>: number of candidates (8)
--radius (optional) <double>: search radius (300)
--error (optional) <double>: GPS error (50)
--log_level (optional) <int>: log level (2)
--output_fields (optional) <string>: Output fields
  opath,cpath,tpath,ogeom,mgeom,pgeom,
  offset,error,spdist,tp,ep,all
For xml configuration, check example folder
------------    Program finished     ------------
```

### Run python script

Run in bash
```
    # Change to the `example/python` folder which contains fmm_test.py
    cd ../example/python
    python fmm_test.py
```

If you have any installation error, refer to [Q&A](/docs/installation/qa).
