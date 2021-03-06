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

Note
{: .label .label-blue }
All the commands listed below should be executed **under the cygwin terminal** instead of
the windows cmd terminal.

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
You check the path of the `fmm` folder by typing `pwd` on the terminal.

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

It will also create a folder `python` under the build path, which contains fmm bindings (`fmm.py` and `_fmm.so`) that are installed into Python site-packages location (e.g., `/usr/lib/python2.7/dist-packages`).

Since a shared library is installed into `/usr/local/lib`, that path must be added to the `PATH` variable in cygwin.  

```
echo 'export PATH=/usr/local/lib:$PATH' >> ~/.bash_profile
source ~/.bash_profile
```

## Verfication of installation

### Verify c++ program  
Open a **cygwin-terminal** terminal and type `fmm`, you should see the following output:
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

### Verify python binding  

In the **cygwin-terminal**, execute the command below
```
    # Change to the `example/python` folder under fmm master directory which contains fmm_test.py
    cd /home/fmm/example/python
    python fmm_test.py
```

If you have any installation error, refer to [Q&A](/docs/installation/qa).
