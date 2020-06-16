---
title: OSM data
nav_order: 4
parent: Tutorial
---

# OSM data

FMM now supports directly reading OSM network.

## Download an OSM file.

Download from the [Geofabrik](https://download.geofabrik.de/index.html), clip for a smaller region using [osmconvert](https://wiki.openstreetmap.org/wiki/Osmconvert):  

```
osmconvert country.osm.pbf -b=west_coor,south_coor,east_coor,north_coor -o=region.o5m
```

Note the coordinate of the box is in order of WSEN.

Download from other online resources of OSM.

```
# On Ubuntu
wget https://download.bbbike.org/osm/bbbike/Stockholm/Stockholm.osm.pbf
# On Windows and Mac
curl https://download.bbbike.org/osm/bbbike/Stockholm/Stockholm.osm.pbf -o Stockholm.osm.pbf
```

## Run map matching

```
stmatch --network Stockholm.osm.pbf --gps traj.csv -k 16 -r 0.005 -e 0.0005 --vmax 0.0002 --output mr.txt
```

## Result

![result](/assets/images/result.png){:.img-large}

It is also possible to convert OpenStreetMap network into a routable shapefile.
Check the tutorial at [osm_mapmatching](https://github.com/cyang-kth/osm_mapmatching).
