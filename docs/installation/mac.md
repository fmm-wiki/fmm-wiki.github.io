---
layout: default
title: Mac
parent: Installation
nav_order: 4
---

## Mac platform

Install requirements with
```
  brew install boost gdal libomp
```

Install the C++ program with

```
  # Under the project folder
  mkdir build
  cd build
  cmake ..
  make
  sudo make install
```

Install python extension with

```
    cd python
    mkdir build
    cd build
    cmake ..
    make
```
