---
title: Installation
nav_order: 2
has_children: true
---

# Installation

The C++ program and Python API are installed with Cmake tool.

### C++ command line program

- `ubodt_gen`: the Upper bounded origin destination table (UBODT) generator (precomputation) program
- `fmm`: the program implementing fast map matching algorithm
- `stmatch`: the program implementing STMATCH algorithm, no precomputation needed

### Python API

- fmm: the module contains Network, NetworkGraph, FMM, STMATCH to call the map matching
function in Python.
