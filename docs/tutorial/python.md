---
title: Run fmm in python
nav_order: 2
parent: Tutorial
---

# Run fmm in python

With python extension installed, run fmm in python can be as simple as:

```python
import fmm
# Load model from configuration file
model = fmm.MapMatcher("fmm_config.xml")

# Run map matching with wkt geometry as input

wkt = "LINESTRING (0.200812146892656 2.14088983050848,1.44262005649717 2.14879943502825,3.06408898305084 2.16066384180791,3.06408898305084 2.7103813559322,3.70872175141242 2.97930790960452,4.11606638418078 2.62337570621469)"

result = model.match_wkt(wkt)

# Print the result

print "Matched path geometry",result.mgeom
print "Matched points geometry",result.pgeom
print "Matched edge id",list(result.opath)
print "Matched path edges",list(result.cpath)
```

You can also run fmm in jupyter-notebook as shown in [fmm_demo.ipynb](https://github.com/cyang-kth/fmm/blob/master/python/fmm_demo.ipynb).
