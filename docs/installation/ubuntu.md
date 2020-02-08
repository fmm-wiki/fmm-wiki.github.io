---
layout: default
title: Ubuntu
parent: Installation
nav_order: 2
---

# Ubuntu platform (tested with 16.04)
{: .no_toc }

1. TOC
{:toc}

---

## Install requirements

### Requirements for C++

- C++ Compiler supporting c++11 and OpenMP
- [CMake](https://cmake.org/) >=3.5: cross platform building tools
- [GDAL](http://www.gdal.org/) >= 2.2: IO with ESRI shapefile, Geometry data type
- [Boost Graph](http://www.boost.org/doc/libs/1_65_1/libs/graph/doc/index.html) >= 1.54.0: routing algorithms used in UBODT Generator
- [Boost Geometry](http://www.boost.org/doc/libs/1_65_1/libs/geometry/doc/html/index.html) >= 1.54.0: Rtree, Geometry computation
- [Boost Serialization](https://www.boost.org/doc/libs/1_66_0/libs/serialization/doc/index.html) >= 1.54.0: Serialization of UBODT in binary format

Install the requirements with

```
sudo apt-get install libboost-dev libboost-serialization-dev gdal-bin libgdal-dev make cmake
```

### Requirements for Python

- swig 4.0.0
- Python 2.7

Install requirements with

```
sudo apt-get install swig python-dev
```


## Install program in C++

```
  # Under the project folder
  mkdir build
  cd build
  cmake ..
  make
  sudo make install
```


It will build executable files under the `build` folder, which are installed to `/usr/local/bin`:

- `ubodt_gen`: the Upper bounded origin destination table (UBODT) generator (precomputation) program
- `ubodt_gen_omp`: the parallel Upper bounded origin destination table (UBODT) generator (precomputation) program.
- `fmm`: the map matching program (single processor)
- `fmm_omp`: parallel map matching implemented with OpenMP.

These executable files will be copied into the `~/bin` path, which should be added to the `PATH` variable by default.

## Install python extension



### Installation

1. To install the python extension, under the project folder run
```
    cd python
    mkdir build
    cd build
    cmake ..
    make
```
2. Add the `build` folder to the environment variable `PYTHONPATH` (set the `PATH_TO_BUILD_FOLDER` below to the **absolute path** of the `build` folder, e.g., `/home/Administrator/workspace/fmm/python/build`, you can run `pwd` to check the absolute path of the current folder):
```
    echo 'export PYTHONPATH=${PYTHONPATH}:PATH_TO_BUILD_FOLDER' >> ~/.bashrc
    source ~/.bashrc
```

### Verification of installation

Run (from the `build` folder)

```
    # Change to the parent folder which contains fmm_test.py
    cd ..
    python fmm_test.py
```

## Verfication of installation

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
