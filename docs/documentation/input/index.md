---
layout: default
title: Input
nav_order: 3
parent: Documentation
---

# Input and output
{: .no_toc }

1. TOC
{:toc}

---

## GPS data

GPS trajectory data should be stored in one of the two format:
- an ESRI shapefile where each feature stores a trajectory. The id field name will be specified by the user.
- a CSV file with a header row and columns separated by `;`. Each row stores a trajectory with geometry in [WKT linestring format](https://en.wikipedia.org/wiki/Well-known_text_representation_of_geometry). The id and geometry column name will be specified by the user. An example can be found at [trips.csv](https://github.com/cyang-kth/fmm/blob/master/example/data/trips.csv)

## Network data

Network data should be stored in ESRI shapefile, each row stores a network edge with **id, source and target fields**, which defines the topology of network graph.

For more details, please to refer to the [configuration](/docs/documentation/configuration) page.
