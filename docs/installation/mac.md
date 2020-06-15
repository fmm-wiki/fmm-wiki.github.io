---
title: Mac
parent: Installation
nav_order: 4
---

# Mac platform
{: .no_toc }

1. TOC
{:toc}
---

## Install requirements


1. Requirements  
- C++ Compiler supporting c++11 and OpenMP
- [CMake](https://cmake.org/) >=3.5: cross platform building tools
- [GDAL](http://www.gdal.org/) >= 2.2: IO with ESRI shapefile, Geometry data type
- [Boost Graph](http://www.boost.org/doc/libs/1_65_1/libs/graph/doc/index.html) >= 1.54.0: routing algorithms used in UBODT Generator
- [Boost Geometry](http://www.boost.org/doc/libs/1_65_1/libs/geometry/doc/html/index.html) >= 1.54.0: Rtree, Geometry computation
- [Boost Serialization](https://www.boost.org/doc/libs/1_66_0/libs/serialization/doc/index.html) >= 1.54.0: Serialization of UBODT in binary format
- [Libosmium](https://github.com/osmcode/libosmium): a library for reading OpenStreetMap data. It requires expat and bz2.  
- [swig](http://www.swig.org/): used for building Python bindings.

```
  brew install boost gdal libomp expat bzip2
```

## Install C++ program and Python bindings

1. Build and install the program with cmake
```
  # Under the project folder
  mkdir build
  cd build
  cmake ..
  make -j4
  sudo make install
```
It will build executable files under the `build` folder, which are installed to `/usr/local/bin`:
- `ubodt_gen`: the Upper bounded origin destination table (UBODT) generator (precomputation) program
- `fmm`: the program implementing fast map matching algorithm
- `stmatch`: the program implementing STMATCH algorithm, no precomputation needed

It will also create a folder `python` under the build path, which contains library that can
be imported into Python. In order to import fmm successfully and that folder must be added to the environment variable `PYTHONPATH`.

Add the `build/python` folder to the environment variable `PYTHONPATH` (set the `PATH_TO_BUILD_PYTHON_FOLDER` below to the **absolute path** of the `build/python` folder, e.g., `/home/Administrator/workspace/fmm/build/python`, you can run `pwd` to check the absolute path of the current folder):
```
    echo 'export PYTHONPATH=${PYTHONPATH}:PATH_TO_BUILD_FOLDER' >> ~/.bashrc
    source ~/.bashrc
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
--pf (optional) <double>: penalty factor (0)
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
    # Change to the parent folder which contains fmm_test.py
    cd ../example/python
    python fmm_test.py
```

If you have any installation error, refer to [Q&A](/docs/installation/qa).
