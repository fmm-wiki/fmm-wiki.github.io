---
title: Web demo
nav_order: 3
parent: Tutorial
---

# Run a web demo

1. Running a web demo for fmm requires the fmm python extension and python dependency
- flask
- tornado
Install those packages with
```
pip install flask tornado
```

2. Prepare a JSON configuration

STMATCH web app configuration
```
{
  "input": {
    "network": {
      "file": "network.shp",
      "id": "ID"
    }
  },
  "model": "stmatch",
  "parameters": {
    "k": 32,
    "r": 0.01,
    "e": 0.003
  }
}
```

FMM web app configuration
```
{
  "input": {
    "network": {
      "file": "network.shp",
      "id": "ID"
    },
    "ubodt":{
      "file": "ubodt.txt"
    }
  },
  "model": "fmm",
  "parameters": {
    "k": 32,
    "r": 0.01,
    "e": 0.003
  }
}
```

3. Run the `fmm_web_app.py` in the [web_demo](https://github.com/cyang-kth/fmm/tree/master//example/web_demo)
```bash
# change to directory web_demo from the project folder
cd example/web_demo
# Start the web demo app
python fmm_web_app.py -c stmatch_config.json
```

Check [osm_mapmatching](https://github.com/cyang-kth/osm_mapmatching) for a concrete example.
