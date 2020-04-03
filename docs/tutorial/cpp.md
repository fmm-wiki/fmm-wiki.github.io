---
title: Command line program
nav_order: 1
parent: Tutorial

---

# Command line program
{: .no_toc }

1. TOC
{:toc}

---

### Change work directory to the example/command_line_example folder.

```bash
# cd to the example folder
cd example/command_line_example
```

Warning
{: .label .label-yellow }

For `fmm`, it takes an ubodt file that can be generated using the `ubodt_gen`.

### Precompute UBODT

  ```bash
  # XML configuration
  ubodt_gen ubodt_config.xml
  # Command line arguments
  ubodt_gen --network ../data/edges.shp --output ubodt.txt --delta 3
  ```

  Link to [ubodt_config.xml](https://github.com/cyang-kth/fmm/blob/master/example/command_line_example/ubodt_config.xml)

### Precompute UBODT parallelly

  ```bash
  # XML configuration
  ubodt_gen ubodt_config_omp.xml
  # Command line arguments
  ubodt_gen --network ../data/edges.shp --output ubodt.txt --delta 3 --use_omp
  ```

  Link to [ubodt_config_omp.xml](https://github.com/cyang-kth/fmm/blob/master/example/command_line_example/ubodt_config_omp.xml)

### Matching GPS trajectory in shapefile using fmm

  ```bash
  # XML configuration
  fmm fmm_config.xml
  # Command line arguments
  fmm --ubodt ubodt.txt --network ../data/edges.shp --gps ../data/trips.shp -k 4 -r 0.4 -e 0.5 --output mr.txt
  ```

  Link to [fmm_config.xml](https://github.com/cyang-kth/fmm/blob/master/example/command_line_example/fmm_config.xml)

### Matching GPS trajectory in shapefile using stmatch

  ```bash
  # XML configuration
  # XML configuration
  stmatch stmatch_config.xml
  # Command line arguments
  stmatch --network ../data/edges.shp --gps ../data/trips.shp -k 4 -r 0.4 -e 0.5 --output mr.txt
  ```

  Link to [stmatch_config.xml](https://github.com/cyang-kth/fmm/blob/master/example/command_line_example/stmatch_config.xml)

### Matching GPS trajectory in CSV file using fmm

  ```bash
  # XML configuration
  fmm fmm_config_csv_trajectory.xml
  # Command line arguments
  fmm --ubodt ubodt.txt --network ../data/edges.shp --gps ../data/trips.csv -k 4 -r 0.4 -e 0.5 --output mr.txt
  ```

  Link to [fmm_config_csv_trajectory.xml](https://github.com/cyang-kth/fmm/blob/master/example/command_line_example/fmm_config_csv_trajectory.xml)

### Matching GPS Points in CSV file using fmm  

  ```bash
  # XML configuration
  fmm fmm_config_csv_point.xml
  # Command line arguments
  fmm --ubodt ubodt.txt --network ../data/edges.shp --gps ../data/gps.csv --gps_point -k 4 -r 0.4 -e 0.5 --output mr.txt
  ```

  Link to [fmm_config_csv_point.xml](https://github.com/cyang-kth/fmm/blob/master/example/command_line_example/fmm_config_csv_point.xml)

### Parallel map matching

  ```bash
  # XML configuration
  fmm fmm_config_omp.xml
  # Command line arguments
  fmm --ubodt ubodt.txt --network ../data/edges.shp --gps ../data/gps.csv --gps_point -k 4 -r 0.4 -e 0.5 --output mr.txt --use_omp
  ```

  Link to [fmm_config_omp.xml](https://github.com/cyang-kth/fmm/blob/master/example/command_line_example/fmm_config_omp.xml)

### Customized output fields

  ```bash
  # XML configuration
  fmm fmm_config_output_fields.xml
  # Command line arguments
  fmm --ubodt ubodt.txt --network ../data/edges.shp --gps ../data/gps.csv --gps_point -k 4 -r 0.4 -e 0.5 --output mr.txt --output_fields opath,cpath,mgeom,tpath,spdist
  ```

  Link to [fmm_config_output_fields.xml](https://github.com/cyang-kth/fmm/blob/master/example/command_line_example/fmm_config_output_fields.xml)
