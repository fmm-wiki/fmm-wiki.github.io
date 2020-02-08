---
title: Run a web demo
nav_order: 3
parent: Tutorial
---

# Run a web demo

Running a web demo for fmm requires the fmm python extension and python dependency

- flask
- tornado

Install those packages with
```
pip install flask tornado
```

Run the `fmm_web_app.py` in the [web_demo](https://github.com/cyang-kth/fmm/tree/master/web_demo) with fmm_web_config.xml.

```bash
# change to directory web_demo from the project folder
cd web_demo
# Start the web demo app
python fmm_web_app.py -c fmm_web_config.xml
```

Check [osm_mapmatching](https://github.com/cyang-kth/osm_mapmatching) for a concrete example.
