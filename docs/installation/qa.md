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
If you have multiple version of Python installed, you can specify a specific version with
```
cmake .. -DPYTHON_LIBRARY=/anaconda2/lib/libpython2.7.dylib
```
1. ImportError: dynamic module does not define init function (init_fmm)
```
ImportError: dynamic module does not define init function (init_fmm)
```
It may be caused by multiple version of Python installed, check the issue above.
1. ImportError: No module named fmm  
```
  File "fmm_test.py", line 1, in <module>
    import fmm
  ImportError: No module named fmm
```
Make sure that the `build` folder is added to the environment variable `PYTHONPATH` as shown above (step 2 of installation).
