---
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

GPS trajectory data should be stored in one of the three formats:
- GDAL trajectory file: an ESRI shapefile where each feature stores a trajectory. The id field name will be specified by the user.  
An example can be found at [trips.shp](https://github.com/cyang-kth/fmm/blob/master/example/data/trips.shp)  
- CSV trajectory file: a CSV file with a header row and columns separated by `;`. Each row stores a trajectory with id (integer), geometry in [WKT linestring format](https://en.wikipedia.org/wiki/Well-known_text_representation_of_geometry) and timestamp(optional, a sequence of intergers). The id, geometry and timestamp column names will be specified by the user.  
An example can be found at [trips.csv](https://github.com/cyang-kth/fmm/blob/master/example/data/trips.csv)  
- CSV point file: a CSV file with a header row and columns separated by `;`. Each row stores a single observation containing id(integer), x(longitude), y(latitude), timestamp(optional, integer). The file must be sorted already by id and timestamp (trajectory will be passed). The id, x, y and timestamp column names will be specified by the user.  
Examples can be found at [gps.csv](https://github.com/cyang-kth/fmm/blob/master/example/data/gps.csv) and [gps_timestamps.csv](https://github.com/cyang-kth/fmm/blob/master/example/data/gps_timestamps.csv).

## Network data

Network data should be stored in ESRI shapefile. Each feature should store a network edge with **id, source and target fields**, which define the topology of network graph.

As shown below in solid line below:

![Network](/assets/images/network.png){:.img-large}

Check the [example](/docs/example). For more details, please to refer to the [configuration](/docs/documentation/configuration) page.

## Convert road network in shapefile from/to CSV format

ESRI shapefile can be conveniently converted from/to CSV file using [GDAL program](https://gdal.org/programs/index.html).

1. Convert from shapefile to CSV  
```bash
ogr2ogr -f "CSV" edges.csv edges.shp -lco GEOMETRY=AS_WKT
```
It will generate a csv file called `edges.csv` with content of (digits of float are removed)
```
WKT,_uid_,id,source,target,cost,x1,y1,x2,y2
"LINESTRING (2 1,2 0)","1","1","1","2",1,2,1,2,0
"LINESTRING (2 0,2 1)","2","2","2","1",1,2,0,2,1
"LINESTRING (3 1,2 1)","3","3","3","1",1,3,1,2,1
"LINESTRING (4 1,3 1)","4","4","4","3",1,4,1,3,1
```

2. Convert from CSV to shapefile  
Create a `convert.vrt` file containing the input CSV file and the fields (**the OGRVRTLayer name should be the same name as the csv file**).

```xml
<OGRVRTDataSource>
    <OGRVRTLayer name="edges">
        <SrcDataSource>edges.csv</SrcDataSource>
        <GeometryType>wkbLineString</GeometryType>
        <Field name="id" src="id" />
        <Field name="source" src="source" />
        <Field name="target" src="target" />
        <GeometryField encoding="WKT" field='WKT' > </GeometryField >
    </OGRVRTLayer>
</OGRVRTDataSource>
```

Then execute  
```bash
ogr2ogr -f "ESRI Shapefile" edges2.shp convert.vrt
```
It will generate a new shapefile called edges2.shp.
