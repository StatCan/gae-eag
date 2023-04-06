# DAS-SAD GAE-EAG documentation and notebooks

---

## GAE User Guide: https://statcan.github.io/gae-eag/

---

## Notebooks:

### Cloning Portal Items-(reusable).ipynb
  This Python code uses the ArcGIS Python API to clone an item from one ArcGIS Portal (the source) to another (or the same one). The _copy_data_ parameter is set to _True_ to ensure that any associated data is also cloned. However, it is important to note that ESRI limitations may cause the code to fail.

### Create Map(s) in Notebook(s).ipynb
  This code provides a simple way to retrieve and map data from DAS-GAE ArcGIS portal using Python.  Maps can be created using ESRI or Open Source packages.

### Geocoding on DAS via Python API (reusable).ipynb
  The code connects to the DAS-GAE ArcGIS Portal, and then demonstrates different ways of geocoding addresses using STC Datasources. The geocoder is in a __pilot stage__; therefore, results may be inaccurate and/or not precise. Proceed with caution!

### PostgreSQL connection (reusable).ipynb
  This code is used to pull data from a DAS-GAE PostgreSQL+PostGIS database into a Python notebook for further analysis.
