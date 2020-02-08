---
title: Configuration
nav_order: 4
parent: Documentation
---

# Configuration
{: .no_toc }

1.  TOC
{:toc}

---

# XML

## fmm

| `fmm_config/`          | Type   | Option   | Description                                                                                             |
| ---------------------- | ------ | -------- | ------------------------------------------------------------------------------------------------------- |
| `input/ubodt/file`     | String | Required | ubodt file name                                                                                         |
| `input/ubodt/delta`    | float  | Optional | upper-bound of distances in ubodt (default infered from file)                                           |
| `input/network/file`   | String | Required | network file name                                                                                       |
| `input/network/id`     | String | Optional | network id field name (default:`id`)                                                                    |
| `input/network/source` | String | Optional | network source field name (default:`source`)                                                            |
| `input/network/target` | String | Optional | network target field name (default:`target`)                                                            |
| `input/gps/file`       | String | Required | GPS file name                                                                                           |
| `input/gps/id`         | String | Optional | GPS id field/column name (default:`id`)                                                                 |
| `input/gps/geom`       | String | Optional | GPS geometry field/column name (default:`geom`), only applicable for CSV file                           |
| `parameters/k`         | int    | Optional | number of candidates  (default:`8`)                                                                     |
| `parameters/r`         | float  | Optional | search radius  (default:`300`)                                                                          |
| `parameters/gps_error` | float  | Optional | GPS sensor error  (default:`50`)                                                                        |
| `output/file`          | String | Required | Output file name                                                                                        |
| `output/fields`        | String | Required | [Output fields](/docs/documentation/output/) name, one or more in (opath,cpath,tpath,ogeom,mgeom, pgeom,offset,error,spdist,tp,ep,all) |
| `other/log_level`      | int    | Optional | Log level  (default:`2`(info)). `0`-trace,`1`-debug,`2`-info,`3`-warn,`4`-err,`5`-critical,`6`off|

Warning
{: .label .label-yellow }

-   About spatial unit. The unit of search radius and gps error are assumed to be the same as the road network shapefile.
    -   Both the network and gps data should be in the same reference system.
    -   If both the network and gps data are unprojected (in geodetic degree such as OSM and latitude, longitude), then 1 degree of latitude or longitude equals to about 111km. Search radius of `0.003` should be defined here to represent to 300 meters in reality.
    -   If both the network and gps data are projected in meters, Search radius of `300` corresponds to 300 meters in reality.

An example can be

```xml
<?xml version="1.0" encoding="utf-8"?>
<fmm_config>
  <input>
    <ubodt>
      <file>ubodt.txt</file>
    </ubodt>
    <network>
      <file>data/edges.shp</file>
      <id>id</id>
    </network>
    <gps>
      <file>data/trips.shp</file>
      <id>id</id>
    </gps>
  </input>
  <parameters>
    <k>4</k>
    <r>0.4</r>
    <pf>0</pf>
    <gps_error>0.5</gps_error>
  </parameters>
  <output>
    <fields>
      <all/>
    </fields>
    <file>mr.txt</file>
  </output>
  <other>
    <log_level>2</log_level>
  </other>
</fmm_config>
```

## ubodt_gen

| `ubodt_config/`        | Type   | Option   | Description                                  |
| ---------------------- | ------ | -------- | -------------------------------------------- |
| `input/network/id`     | String | Optional | network id field name (default:`id`)         |
| `input/network/source` | String | Optional | network source field name (default:`source`) |
| `input/network/target` | String | Optional | network target field name (default:`target`) |
| `parameters/delta`     | float  | Optional | Upper distance of routing (default:`3000`)   |
| `output.file`          | String | Required | Output file name                             |
| `other/log_level`      | int    | Optional | Log level  (default:`2`(infor)), `0`-trace,`1`-debug,`2`-info,`3`-warn,`4`-err,`5`-critical,`6`-off |

Warning
{: .label .label-yellow }

-   **Delta** should be specified in the same spatial unit as the network file. If the reference system is WGS84 (in degree), then 1 degree of latitude or longitude equals to about 111km. It is suggested to try some small values first (e.g., 0.01 degree).

An example is provided as

```xml
<?xml version="1.0" encoding="utf-8"?>
<ubodt_config>
    <input>
        <network>
            <file>data/edges.shp</file>
            <id>id</id>
            <source>source</source>
            <target>target</target>
        </network>
    </input>
    <parameters>
        <delta>3</delta>
    </parameters>
    <output>
        <file>ubodt.txt</file>        
    </output>
</ubodt_config>
```

# Argument list

## fmm

| Argument          | Type   | Option   | Description                  |
| ----------------- | ------ | -------- | ---------------------------- |
| `--ubodt`         | string | required | Ubodt file name              |
| `--network`       | string | required | Network file name            |
| `--gps`           | string | required | GPS file name                |
| `--output`        | string | required | Output file name             |
| `--network_id`    | string | optional | Network id name (id)         |
| `--source`        | string | optional | Network source name (source) |
| `--target`        | string | optional | Network target name (target) |
| `--gps_id`        | string | optional | GPS id name (id)             |
| `--gps_geom`      | string | optional | GPS geometry name (geom)     |
| `--candidates`    | int    | optional | number of candidates (8)     |
| `--radius`        | double | optional | search radius (300)          |
| `--error`         | double | optional | GPS error (50)               |
| `--log_level`     | int    | optional | log level (2)                |
| `--output_fields` | string | optional | Output fields                |

## ubodt_gen

| Argument      | Type   | Option   | Description                  |
| ------------- | ------ | -------- | ---------------------------- |
| `--network`   | string | required | Network file name            |
| `--output`    | string | required | Output file name             |
| `--id`        | string | optional | Network id name (id)         |
| `--source`    | string | optional | Network source name (source) |
| `--target`    | string | optional | Network target name (target) |
| `--delta`     | float  | optional | upperbound (3000)            |
| `--log_level` | int    | optional | log level (2)                |
