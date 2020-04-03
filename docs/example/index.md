---
title: Example
nav_order: 5
---

# Example

Sample data and configuration can be downloaded from [example folder](https://github.com/cyang-kth/fmm/tree/master/example) at fmm github repo.

- Road network: `data/edges.*`: the road network shapefile where each feature stores an edge with id, source node, target node
- GPS trajectory: `data/trips.*`: the GPS data can be stored as a Shapefile or CSV file.
  + Shapefile: a GPS trajectory file where each feature stores a line representing a noisy GPS trajectory
  + CSV: a CSV file, where each rows stores a wkt linestring.
- Configuration: `*_config.xml`

![fmm output](/assets/images/network.png){:.img-large}

To run map matching on the example data, please to refer to the [command line program](/docs/tutorial/cpp) page. 
