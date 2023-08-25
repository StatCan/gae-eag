# Création de visualisations dans les notebooks (Python)

Lors de la création de visualisations de cartes dans un notebook, vous avez le choix entre utiliser l'API propriétaire ArcGIS pour Python, des bibliothèques Python open source telles que GeoPandas et Matplotlib, ou adopter une approche hybride qui combine les deux. L'API ArcGIS offre des capacités géospatiales étendues et une intégration avec les produits ArcGIS, tandis que les bibliothèques open source offrent une flexibilité et un soutien communautaire. L'approche hybride vous permet de tirer parti des points forts des deux options en fonction de vos besoins et de vos préférences spécifiques.

??? example "Utilisation de méthodes open source"

	1. Installez les packages Python requis pour l'analyse géospatiale, tels que `geopandas`, `folium` ou `matplotlib`.
	2. Importez les modules nécessaires dans votre notebook Python.
	3. Lisez ou importez les données géospatiales dans une structure de données adaptée.
	4. Visualisez les données à l'aide des fonctions ou classes de cartographie du package choisi.
	5. Personnalisez les propriétés de la carte, telles que les couleurs, la symbologie ou les fonds de carte.
	6. Ajoutez des couches ou des annotations supplémentaires à la carte, si nécessaire.
	7. Exportez la carte dans un format souhaité ou affichez-la dans le notebook.
	8. Enregistrez la carte ou partagez-la avec d'autres sous forme d'image ou de fichier HTML interactif.

	Exemple de code utilisant `geopandas` et `matplotlib` :

	```python
	import geopandas as gpd
	import matplotlib.pyplot as plt

	# Lire les données géospatiales
	data = gpd.read_file("chemin_vers_shapefile.shp")

	# Visualiser les données sur une carte
	data.plot()

	# Personnaliser les propriétés de la carte
	plt.title("Ma carte géospatiale")
	plt.xlabel("Longitude")
	plt.ylabel("Latitude")

	# Exporter la carte
	plt.savefig("chemin_vers_fichier_sortie.png", dpi=300)

	# Afficher la carte dans le notebook
	plt.show()
	```

	
??? example  "Utilisation de la méthode de l'API ArcGIS"
	Utilisation d'un produit payant d'ArcGIS

	1. Importez les modules ArcGIS nécessaires dans votre notebook Python.
	2. Connectez-vous à votre compte ArcGIS ou à votre portail en utilisant les informations d'identification appropriées.
	3. Créez un objet de carte en utilisant le module `arcgis.mapping`.
	4. Ajoutez les couches ou les données souhaitées à la carte.
	5. Personnalisez les propriétés de la carte, telles que l'étendue, l'échelle et la symbologie.
	6. Facultativement, ajoutez des étiquettes, des légendes ou d'autres éléments cartographiques.
	7. Exportez la carte dans un format souhaité ou affichez-la dans le notebook.
	8. Enregistrez la carte ou partagez-la avec d'autres utilisateurs via la plateforme ArcGIS.

	Exemple de code :

	```python
	import arcpy
	from arcgis.gis import GIS
	import arcgis.mapping as mapping

	# Connectez-vous à votre compte ArcGIS ou à votre portail
	gis = GIS("https://geoanalyticsdev.cloud.statcan.ca/portal", client_id=' ')
	# Une fenêtre d'authentification s'ouvrira

	# Créez une nouvelle carte
	map = mapping.Map()

	# Ajoutez des couches ou des données à la carte
	map.add_layer("chemin_vers_couche1")
	map.add_layer("chemin_vers_couche2")

	# Personnalisez les propriétés de la carte
	map.zoom_to_layer("chemin_vers_couche1")
	map.legend = True

	# Exportez la carte
	map.export("chemin_vers_fichier_sortie.jpg", resolution=300)

	# Affichez la carte dans le notebook
	map
	```

??? example "Utilisation d'ArcPy"

	1. Assurez-vous d'utiliser la version ArcGIS de Jupyter Notebook pour faciliter son utilisation. Accédez à Démarrer > ArcGIS > Jupyter Notebook. Cela évitera de devoir modifier votre environnement système et vos chemins d'accès.
	2. Importez les modules ArcPy nécessaires dans votre notebook Python.
	3. Connectez-vous à votre compte ArcGIS ou à votre portail en utilisant les informations d'identification appropriées.
	4. Définissez l'espace de travail sur l'emplacement de vos données géospatiales.
	5. Créez un objet de document de carte en utilisant le module `arcpy.mapping`.
	6. Ajoutez les couches ou les données souhaitées à la carte.
	7. Personnalisez les propriétés de la carte, telles que l'étendue, l'échelle et la symbologie.
	8. Facultativement, ajoutez des étiquettes, des légendes ou d'autres éléments cartographiques.
	9. Exportez la carte dans un format souhaité ou affichez-la dans le notebook.
	10. Enregistrez la carte ou partagez-la avec d'autres utilisateurs via la plateforme ArcGIS.

	Exemple de code :

	```python
	import arcpy
	import arcpy.mapping as mapping

	# Définissez l'espace de travail sur l'emplacement de vos données géospatiales
	arcpy.env.workspace = "chemin_vers_l'espace_de_travail"

	# Créez un nouveau document de carte
	mxd = mapping.MapDocument()

	# Ajoutez des couches ou des données à la carte
	df = mapping.ListDataFrames(mxd)[0]
	couche1 = mapping.Layer("chemin_vers_couche1")
	couche2 = mapping.Layer("chemin_vers_couche2")
	mapping.AddLayer(df, couche1)
	mapping.AddLayer(df, couche2)

	# Personnalisez les propriétés de la carte
	df.zoomToSelectedFeatures()
	df.legend.title = "Légende"
	df.titleText = "Ma carte"

	# Exportez la carte
	mapping.ExportToJPEG(mxd, "chemin_vers_fichier_sortie.jpg", resolution=300)

	# Affichez la carte dans le notebook
	mxd
	```
	**[En savoir plus sur ArcPy](https://pro.arcgis.com/fr/pro-app/latest/arcpy/main/arcgis-pro-arcpy-reference.htm)

<br>

Les packages de visualisation open source courants incluent :

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

Ces bibliothèques offrent différents niveaux de fonctionnalités et d'options de personnalisation, vous permettant de choisir celle qui correspond le mieux à vos besoins et préférences.
