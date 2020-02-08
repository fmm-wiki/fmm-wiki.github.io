---
title: Output
nav_order: 4
parent: Documentation
---

# Output
{: .no_toc }

1. TOC
{:toc}

---

## Output of fmm

The output of program `fmm` is a CSV file containing the following information based on user specification:


| Output fields | Type           | Description                                                      |
|---------------|----------------|------------------------------------------------------------------|
| id            | int            | trajectory id                                                    |
| ogeom         | string         | original trajectory geometry                                     |
| opath         | list of int    | edge matched to each point in trajectory                         |
| error         | list of floats | distance from each point to its matched point                    |
| offset        | list of floats | distance from the matched point to the start of the matched edge |
| length        | list of floats | length of the matched edge for each point                        |
| spdist        | list of floats | shortest path distances traversed between consecutive points     |
| pgeom         | string         | a line connecting the matched points                             |
| cpath         | list of int    | the path traversed by the trajectory                             |
| tpath         | list of int    | edges traversed between consecutive points separated by `        |
| mgeom         | string         | the geometry of the cpath                                        |
| ep            | list of floats | emission probability in HMM for each matched point               |
| tp            | list of floats | transition probability in HMM for two consecutive matched points |

By default, only `cpath` and `mgeom` are exported. The fields are illusrated by the image below.

![fmm output](/assets/images/demo1.png){: .img-large}

## Output of ubodt_gen

The output of program `ubodt_gen` is a CSV file or a Binary file, which is automatically detected from the file extension `csv` or `bin`. Binary file can be used to save space in case of a large road network.

The CSV file contains the following information:

| Columns | Type  | Description                                            |
|---------|-------|--------------------------------------------------------|
| source  | int   | index of source node                                   |
| target  | int   | index of target node                                   |
| next_n  | int   | index of next node index visited from source to target |
| prev_n  | int   | index of the node visited before target                |
| next_e  | int   | index of next edge visited from source to target       |
| dist    | float | shortest path distance from source to target           |

Note
{: .label .label-blue}
In UBODT, all the integers are stored as index of nodes or edges, the actual id of edge
will be retrieved from the road network in map matching.  
