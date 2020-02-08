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

1. Install [cygwin](https://www.cygwin.com/) and [apt-cyg](https://github.com/transcode-open/apt-cyg).  
After you have installed cygwin, open the cygwin-terminal and run the following scripts to install apt-cyg.
```
  wget https://raw.githubusercontent.com/transcode-open/apt-cyg/master/apt-cyg
  chmod +x apt-cyg
  mv apt-cyg /usr/local/bin
```
2. Install libraries using apt-cyg
```
  apt-cyg install make gcc-g++ cmake gdal libboost-devel libgdal-devel
```
3. For python extension
```
  apt-cyg install swig python-devel
```

## Install C++ program

1. Build and install the program with cmake
```
  # Under the fmm project folder
  mkdir build
  cd build
  cmake -G "Unix Makefiles" ..
  make
  make install
```
2. Verification of installation
In the cyg-win terminal, type
```
  fmm
```
You should see
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
--pf (optional) <double>: penalty factor (0)
--log_level (optional) <int>: log level (2)
--output_fields (optional) <string>: Output fields
  opath,cpath,tpath,ogeom,mgeom,pgeom,
  offset,error,spdist,tp,ep,all
For xml configuration, check example folder
------------    Program finished     ------------
```

## Install python extension

1. Build with cmake  
To install the python extension, under the project folder run
```
    cd python
    mkdir build
    cd build
    cmake ..
    make
```

2. Verification of installation  
Run (from the `build` folder)
```
    # Change to the parent folder which contains fmm_test.py
    cd ..
    python fmm_test.py
```
