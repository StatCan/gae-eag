#Creating Visuals in Notebooks (python)

When creating map visuals in a notebook, you can choose between using the proprietary ArcGIS API for Python, open-source Python libraries like GeoPandas and Matplotlib, or adopting a hybrid approach that combines both. The ArcGIS API offers extensive geospatial capabilities and integration with ArcGIS products, while open-source libraries provide flexibility and community support. The hybrid approach allows you to leverage the strengths of both options based on your specific needs and preferences.

??? example "Using Open Source Methods"

	1. Install the required Python packages for geospatial analysis, such as `geopandas`, `folium`, or `matplotlib`.
	2. Import the necessary modules in your Python notebook.
	3. Read or import the geospatial data into a suitable data structure.
	4. Visualize the data using the chosen package's mapping functions or classes.
	5. Customize the map properties, such as colors, symbology, or basemaps.
	6. Add additional layers or annotations to the map, if needed.
	7. Export the map to a desired format or display it in the notebook.
	8. Save the map or share it with others as an image or interactive HTML file.

	Example code using `geopandas` and `matplotlib`:

	```python
	import geopandas as gpd
	import matplotlib.pyplot as plt

	# Read the geospatial data
	data = gpd.read_file("path_to_shapefile.shp")

	# Visualize the data on a map
	data.plot()

	# Customize the map properties
	plt.title("My Geospatial Map")
	plt.xlabel("Longitude")
	plt.ylabel("Latitude")

	# Export the map
	plt.savefig("path_to_output_file.png", dpi=300)

	# Display the map in the notebook
	plt.show()
	```
	
??? example "Using ArcGIS API Method"
	Using ArcGIS Paid Product

	1. Import the necessary ArcGIS modules in your Python notebook.
	2. Connect to your ArcGIS account or portal using appropriate credentials.
	3. Create a map object using the `arcgis.mapping` module.
	4. Add desired layers or data to the map.
	5. Customize the map properties, such as extent, scale, and symbology.
	6. Optionally, add labels, legends, or other cartographic elements.
	7. Export the map to a desired format or display it in the notebook.
	8. Save the map or share it with others through the ArcGIS platform.

	Example code:

	```python
	import arcpy
	from arcgis.gis import GIS
	import arcgis.mapping as mapping

	# Connect to your ArcGIS account or portal
	gis = GIS("https://geoanalyticsdev.cloud.statcan.ca/portal", client_id=' ')
	# Authentication pop-up will open

	# Create a new map
	map = mapping.Map()

	# Add layers or data to the map
	map.add_layer("path_to_layer1")
	map.add_layer("path_to_layer2")

	# Customize map properties
	map.zoom_to_layer("path_to_layer1")
	map.legend = True

	# Export the map
	map.export("path_to_output_file.jpg", resolution=300)

	# Display the map in the notebook
	map
	```
??? example "Using ArcPy"

	1. Ensure you are using the ArcGIS version of Jupyter notebook for ease of use. Go to Start > ArcGIS > Jupyter Notebook. This will negate the need to modify your system environment and paths.
	2. Import the necessary ArcPy modules in your Python notebook.
	3. Connect to your ArcGIS account or portal using appropriate credentials.
	4. Set the workspace to the location of your geospatial data.
	5. Create a map document object using the `arcpy.mapping` module.
	6. Add desired layers or data to the map.
	7. Customize the map properties, such as extent, scale, and symbology.
	8. Optionally, add labels, legends, or other cartographic elements.
	9. Export the map to a desired format or display it in the notebook.
	10. Save the map or share it with others through the ArcGIS platform.

	Example code:

	```python
	import arcpy
	import arcpy.mapping as mapping

	# Set the workspace to the location of your geospatial data
	arcpy.env.workspace = "path_to_workspace"

	# Create a new map document
	mxd = mapping.MapDocument()

	# Add layers or data to the map
	df = mapping.ListDataFrames(mxd)[0]
	layer1 = mapping.Layer("path_to_layer1")
	layer2 = mapping.Layer("path_to_layer2")
	mapping.AddLayer(df, layer1)
	mapping.AddLayer(df, layer2)

	# Customize map properties
	df.zoomToSelectedFeatures()
	df.legend.title = "Legend"
	df.titleText = "My Map"

	# Export the map
	mapping.ExportToJPEG(mxd, "path_to_output_file.jpg", resolution=300)

	# Display the map in the notebook
	mxd
	```
	**[Learn more about ArcPY](https://pro.arcgis.com/en/pro-app/latest/arcpy/main/arcgis-pro-arcpy-reference.htm)
	
<br>

Common Open Source Visualization packages include:

- Matplotlib
- Seaborn
- Plotly
- Folium
- GeoPandas
- Bokeh
- Basemap
- Cartopy
- Geoplot
- PySAL

These libraries provide different levels of functionality and customization options, so you can choose the one that best fits your needs and preferences.

