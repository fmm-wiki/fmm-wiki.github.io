---
title: Q&A
parent: Installation
nav_order: 5
---

# Q&A

1. Make error  

If the step `make` fails, make sure that you have all the dependency installed.
For the python API installation, it could be that you have multiple version of Python
installed. Make sure that the default python version
```
which python
```
is the same as the **Python library used in cmake build**, whose location is printed in
the following command.
```
cmake ..  
```

Make sure that the command finds the Python header, library and package for the same Python like this one shown below.

```
-- Python header found at /usr/include/python2.7
-- Python library found at /usr/lib/x86_64-linux-gnu/libpython2.7.so
-- Python packages /usr/lib/python2.7/dist-packages
```

or anaconda case

```
-- Python header found at /anaconda2/include/python2.7
-- Python library found at /anaconda2/lib/libpython2.7.dylib
-- Python packages /anaconda2/lib/python2.7/site-packages
```

If you have multiple version of Python installed, you can manually specify Python position
with (from the docuementation of [cmake](https://cmake.org/cmake/help/v3.0/module/FindPythonLibs.html))

```
cmake .. -DPYTHON_LIBRARY=/anaconda2/lib/libpython2.7.dylib -DPYTHON_INCLUDE_DIR=/anaconda2/include/python2.7
```

You can also post an issue at [fmm repo](https://github.com/cyang-kth/fmm).
