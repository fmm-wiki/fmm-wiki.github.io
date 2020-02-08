---
title: Run fmm in C++
nav_order: 1
parent: Tutorial
---

## Run fmm in C++
The programs take configuration in xml format as input

```bash
# cd to the example folder
cd example

# Run ubodt_gen with xml configuration
ubodt_gen ubodt_config.xml

# or Run ubodt in command line
ubodt_gen --network data/edges.shp --id id --source source --target target --output ubodt.txt --delta 4.0    

# Run fmm with xml configuration
fmm fmm_config.xml

# Run fmm or fmm_omp in command line
fmm --ubodt ubodt.txt --network data/edges.shp --gps data/trips.csv --output mr.txt --candidates 4 --radius 0.4 --error 0.5

# Run the parallelized version
ubodt_gen_omp ubodt_config.xml
fmm_omp fmm_config.xml
```

Check the [example](/docs/example) folder for two sample configuration files and [configuration](/docs/documentation/configuration) for documentation.

If you want to write your own C++ program, you can check [fmm.cpp](https://github.com/cyang-kth/fmm/blob/master/app/fmm.cpp) for the detailed procedure of map matching.
