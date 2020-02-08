---
layout: default
title: Common errors
parent: Installation
nav_order: 5
---

# Common error with the installation

1. ImportError: No module named fmm  
```
  File "fmm_test.py", line 1, in <module>
    import fmm
  ImportError: No module named fmm
```
Make sure that the `build` folder is added to the environment variable `PYTHONPATH` as shown above (step 2 of installation).

2. ImportError: dynamic module does not define init function (init_fmm)
```
ImportError: dynamic module does not define init function (init_fmm)
```
It can be caused by multiple version of Python installed. Make sure that the
default python version
```
which python
```
is the same as the Python library used in cmake build. When the following command is executed, the Python location will be printed.
```
cmake ..  
```
If you have multiple version of Python installed, you can specify a specific version with
```
cmake .. -DPYTHON_LIBRARY=/anaconda2/lib/libpython2.7.dylib
```
