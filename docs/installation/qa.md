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
If you have multiple version of Python installed, you can manually specify Python position
with (from the docuementation of [cmake](https://cmake.org/cmake/help/v3.0/module/FindPythonLibs.html))

```
cmake .. -DPYTHON_LIBRARY=/anaconda2/lib/libpython2.7.dylib -DPYTHON_INCLUDE_DIR=/anaconda2/include/python2.7
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
Make sure that the `build/python` folder is added to the environment variable `PYTHONPATH` as shown above (step 2 of installation).

Make sure that when you run the following commands in your terminal. You should see this information in your output (If fmm is downloaded at location `/home/Administrator/workspace/fmm`).

```
echo $PYTHONPATH;
# You should see /home/Administrator/workspace/fmm/build/python
```

1. ImportError: No such file or directory

Make sure that the `build/python` folder is added to the environment variable `PYTHONPATH` as shown above (step 2 of installation).

Make sure that when you run the following commands in your terminal. You should see this information in your output (If fmm is downloaded at location `/home/Administrator/workspace/fmm`).

```
echo $PYTHONPATH;
# You should see /home/Administrator/workspace/fmm/build/python
```

On windows platform (cygwin enviroment), it seems that you also need to add the `build` folder to the `PATH` variable, then run

```
echo $PATH;
# You should see /home/Administrator/workspace/fmm/build
```
