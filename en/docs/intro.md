# A Simple Introduction to GIS

<p align='center'>
<img src="https://i.ibb.co/TrGQv9f/intro.png" alt="html picture">
</p>
__Geospatial analysis is concerned with the quantitative location of important features, known as phenomena.__
  
Geospatial data is data about phenomena that have a location on the surface of the earth. The location may be static (ex- the location of a road, a disaster event, citizens living in poverty), or dynamic (ex- a moving vehicle or pedestrian, the spread of COVID)
<br>

A GIS (Geospatial Information System) helps us analyze spatial relationships and patterns amongst these phenomena. It is particularly useful for visualizing spatial data and reporting results of analysis.

GIS' are composed of both hardware and software components. Due to the large volumes of spatial data and the need to display values on the fly, GIS hardware often have large storage capacities, fast computing speed, and powerful memory. <b>DAS-GAE has been designed meet these users needs.</b>

---

##Why is Geospatial Analysis important?
Geospatial analysis is conducted to:

- Identify spatial patterns and relationships in data.
- Support decision-making in fields like urban planning, disaster response, and environmental management.
- Optimize resource allocation and management.
- Assess and mitigate risks related to natural disasters and public health emergencies.
- Monitor and analyze environmental changes and impacts.

---

##Spatial Data

Spatial data refers to information that has a location or geographic component associated with it. It is **data that has a spatial reference, such as latitude and longitude or a street address**, that allows it to be displayed on a map and analyzed using geographic information system (GIS) software. Spatial data can be broadly classified into two types: vector data and raster data.

1.	**Vector data**: Vector data represents geographic features using points, lines, and polygons. Examples of vector data include:
	- **Points**: addresses, cities, airports, hospitals, and other discrete locations.
	- **Lines**: roads, rivers, railroads, and other linear features.
	- **Polygons**: countries, states, counties, parks, and other areas with well-defined boundaries.

2.	**Raster data**: Raster data represents geographic features as a grid of cells, where each cell has a value that represents some aspect of the feature being represented. Examples of raster data include:
	- Elevation data: digital elevation models (DEMs) and digital terrain models (DTMs).
	- Satellite imagery: aerial photographs, multispectral imagery, and thermal imagery.
	- Climate data: temperature, precipitation, and other weather-related data.
	
Both vector and raster data can be used in a wide range of GIS applications, such as spatial analysis, cartography, and environmental modeling.


A <b>spatial database</b> — also known as a “<b>geodatabase</b>” — is built to capture and store the points, lines, and polygons.

A geodatabase is a type of database used to store and manage geospatial data, including features, attributes, and relationships. It is designed to support the storage, query, and manipulation of geographic data in a way that preserves the spatial and temporal relationships between features. A geodatabase can store many different types of data, including points, lines, polygons, and raster datasets, and it can be used for a wide range of applications, including GIS analysis, map production, and data management. Geodatabases are typically created and managed using specialized software, such as Esri's ArcGIS.

##Geospatial Analysis
###Common methods
- **Spatial querying**: Searching and retrieving data based on specific spatial criteria or spatial relationships.

- **Spatial statistics**: Analyzing patterns, distributions, and relationships within spatial data using statistical techniques.

- **Spatial modeling**: Creating mathematical or computational models to simulate and predict spatial phenomena or processes.

- **Spatial interpolation**: Estimating values at unobserved locations based on known values from neighboring locations.

- **Geocoding**: Converting addresses or place names into geographic coordinates (latitude and longitude).

- **Network analysis**: Examining connectivity, flow, and accessibility within a network, such as transportation or utility networks.

- **Remote sensing**: Analyzing data acquired from satellites, aircraft, or other sensors to study and monitor the Earth's surface.

- **Geostatistics**: Applying statistical methods to analyze and model spatial variability and uncertainty in data.

- **Spatial visualization**: Representing geospatial data through maps, charts, graphs, and other visual formats to facilitate understanding and communication.

These methods are generally used in combination, depending on the specific analysis objectives and the characteristics of the data being studied.

###Projections and Coordinates
Understanding projections and coordinate systems is essential in GIS to ensure accurate representation and analysis of spatial data. By selecting the right projection, considering the map's purpose, and managing distortions effectively, GIS users can work with spatial data accurately and meaningfully.

#### Projections
Map projections are necessary because the Earth's curved surface cannot be perfectly represented on a flat map. This introduces distortions in shape, area, distance, and direction. No projection can eliminate all distortions simultaneously, so choosing an appropriate projection depends on the map's purpose and the properties that need to be maintained or minimized.

Ensuring that all datasets and layers are in the same projection is crucial for accurate and meaningful geospatial analysis, as it allows for proper alignment, measurement consistency, and valid spatial relationships between different geographic features.

In ArcGIS, you can change or reproject data by using the "Project" tool, which allows you to convert data from one coordinate system to another.

In QGIS, you can change or reproject data by using the "Reproject Layer" tool, which enables you to transform data from one coordinate system to another.

In Python, you can perform reprojection of geospatial data using various libraries such as pyproj and gdal.

Commonly used projections:

**Mercator Projection**: The Mercator projection is widely used for world maps, navigation charts, and online mapping applications. ArcGIS/ESRI has adopted a modified version of the Mercator projection called the "Web Mercator Auxiliary Sphere" (WGS 1984 Web Mercator, or Web Mercator for short) as the default projection for web mapping services within their software ecosystem.

**Lambert Conformal Conic projection**: The custom projection used by Statistics Canada is a variant of the Lambert Conformal Conic projection. The Statistics Canada Lambert projection is specifically based on the Lambert Conformal Conic projection, which is a type of conic projection known for preserving local angles and shapes.

#### Coordinate Systems
Coordinate systems provide a reference framework to define locations on the Earth's surface. There are two main types: geographic coordinate systems (latitude and longitude) and projected coordinate systems (X and Y coordinates on a flat map). 
Geographic coordinate systems are spherical and measure positions in latitude and longitude. 
Projected coordinate systems use Cartesian coordinates and are used for accurate measurements and analysis.

##GIS Vocabulary

|Term||Description|
|----||----|
|API||Application Programming Interface - a method for software developers to enable communication between different applications or systems.|
|ArcGIS||A geographic information system (GIS) software suite developed by ESRI.|
|ArcGIS Pro||A desktop GIS application in the ArcGIS suite for advanced geospatial analysis, data management, and visualization.|
|App||Short for "application," referring to software designed to run on PCs, smartphones, tablets, or other web devices.|
|Attribute||Non-spatial information associated with geospatial data, stored in attribute tables.|
|Basemap||GIS data and/or imagery that form the background setting for a map.|
|Buffer||A zone or area created around a geographic feature, often used for proximity analysis.|
|Cartography||The art and science of creating maps, including design, symbolization, and map production.|
|Choropleth Map||A thematic map that uses different shades or patterns to represent data values for specific geographic areas.|
|Coordinates||Values represented by the letters x, y, z [or m (measure)], that define a position within a spatial reference.|
|CRS||Coordinate Reference System - a framework used to define and locate geographic features on the Earth's surface.|
|DCAT, geoDCAT-ap||Metadata standard to make spatial datasets, dataset series, and services searchable on general data catalogs.|
|DEM||Digital Elevation Model - a representation of terrain or surface topography in a digital format.|
|ESRI||Environmental Systems Research Institute, Inc. - a leading company in the GIS industry, known for developing ArcGIS software.|
|EO, Earth Observation||Information about the planet Earth gathered via remote-sensing technologies and by ground-based techniques (ex- satellite or drone imagery).|
|ETL||Procedure of copying data from sources into a destination system which represents the data differently from the source or in a different context than the source.|
|Generalization||Method used in GIS to reduce detail in data (for privacy and/or visualizing).|
|Geocode||The process of identifying a location by one or more attributes, typically address or latitude/longitude, from a layer.|
|Geodatabase||A container or file format used to store, manage, and organize geospatial data in a structured manner.|
|Geographic Information System||A system designed to capture, store, analyze, manage, and present spatial and attribute data.|
|Geoprocessing||The analysis and manipulation of geospatial data using GIS tools and algorithms.|
|Geospatial||Relating to or denoting data that is associated with a specific location on the Earth's surface.|
|HNAP||HNAP-Canada is a profile on Harmonized North American Profile which itself is a profile on ISO19139 (ISO 19115*).|
|IDE||Integrated Development Environment - a software application that provides comprehensive tools for software development.|
|Jupyter Notebook||An open-source web application that allows users to create and share documents containing live code, equations, visualizations, and narrative text.|
|Layer||Thematic data described and stored in a map library. Layers act as transparencies that can be laid atop one another for viewing or spatial analysis.|
|Metadata||Information that describes the characteristics and properties of geospatial data, such as its source, quality, and content.|
|OGC||Open Geospatial Consortium - Open Source champion; Open Standards.|
|PostgreSQL||Open-source object-relational database system; Azure Managed.|
|Projection||A mathematical transformation applied to spatial data to convert it from the Earth's curved surface to a flat surface, typically a map.|
|Python||A popular high-level programming language widely used in geospatial analysis and scripting within the GIS domain.|
|R||A programming language and software environment for statistical computing and graphics, commonly used in data analysis and visualization.|
|Raster||A data format that represents geographic information as a grid of cells or pixels, commonly used for satellite imagery and elevation data.|
|Shapefile||Vector data storage format for storing the location, shape, and attributes. It is stored in a set of 4 related files and contains one feature class. *Shapefiles should be avoided when possible*.|
|Topology||The spatial relationships and connectivity between geometric features within a GIS dataset.|
|Vector||A data format that represents geographic features as points, lines, and polygons using coordinates.|
|Web-Map||An interactive map accessible over the internet, often built using web technologies and geospatial data.|
|WFS||Specifications that standardize data manipulation and map display on the Internet.|
|WMS||Specifications that provide uniform access by Web clients to maps rendered by map servers on the Internet.|
