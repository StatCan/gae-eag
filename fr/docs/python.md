# Python

L'analyse géospatiale utilise principalement Python pour plusieurs raisons :

1. **Écosystème riche de bibliothèques géospatiales** : Python dispose d'une vaste collection de bibliothèques spécialisées en géospatial telles que GeoPandas, Shapely, Fiona et PySAL, qui fournissent des outils puissants pour manipuler des données géospatiales, effectuer des opérations spatiales et réaliser des analyses géospatiales avancées.

2. **Intégration avec d'autres bibliothèques de science des données et d'analyse** : La popularité de Python dans la communauté de la science des données et son vaste écosystème de bibliothèques d'analyse de données telles que NumPy, Pandas et Matplotlib en font un choix idéal pour l'analyse géospatiale. Python permet une intégration transparente de l'analyse géospatiale avec d'autres tâches de traitement et de visualisation des données.

3. **Flexibilité et polyvalence** : Python est un langage de programmation polyvalent connu pour sa flexibilité. Il permet aux utilisateurs de combiner l'analyse géospatiale avec d'autres fonctionnalités telles que l'apprentissage automatique, l'analyse statistique et le développement web. La flexibilité de Python permet la création de flux de travail personnalisés et de solutions adaptées aux besoins spécifiques de l'analyse géospatiale.

4. **Facilité d'utilisation et lisibilité** : Python est réputé pour sa lisibilité et sa syntaxe conviviale. Sa structure de code claire et concise facilite la compréhension et l'écriture de scripts et de flux de travail d'analyse géospatiale, tant pour les débutants que pour les programmeurs expérimentés. La lisibilité de Python contribue à une meilleure collaboration et maintenabilité des projets géospatiaux.

5. **Support actif de la communauté** : Python bénéficie d'une communauté étendue et active d'analystes, de développeurs et de chercheurs géospatiaux qui contribuent au développement et à l'amélioration des bibliothèques et des outils géospatiaux. La disponibilité d'une documentation étendue, de tutoriels et de ressources en ligne facilite l'apprentissage, le dépannage et l'obtention d'une assistance lors de la réalisation de projets d'analyse géospatiale.

Bien que Python soit largement utilisé dans l'analyse géospatiale, il est important de noter que d'autres langages de programmation tels que R, Java et C++ possèdent également leurs propres bibliothèques et écosystèmes géospatiaux. Le choix du langage de programmation dépend en fin de compte des exigences spécifiques du projet, des préférences personnelles et de l'expertise existante.

## Environnements virtuels

??? tip "Meilleure pratique : Travailler avec des environnements virtuels Conda"
    L'utilisation d'environnements virtuels avec Conda peut vous aider à créer des environnements cohérents, reproductibles et isolés pour vos projets, ce qui peut vous faire gagner du temps et éviter les problèmes causés par des dépendances en conflit ou des modifications au niveau du système.
    
    Par exemple, les produits ArcGIS fonctionnent mieux avec *python 3.7*. En créant un environnement ArcGIS séparé, vous pouvez installer la version 3.7 sans causer de conflits avec la version plus récente de Python 3.10.

??? exemple "Créer un nouvel environnement"
    ```python
    conda create --name <nom_env> <package>
    ```
    exemple :
    ```python
    conda create --n geoENV python=3.7
    ```

??? exemple "Activer votre environnement"
    ```python
    conda activate <nom_env>
    ```


## Installation de package(s)

???info "Packages géospatiaux courants disponibles"
    Cette liste n'est pas exhaustive, mais voici quelques-uns des packages courants :
    
    - GeoPandas
    - Shapely
    - Fiona
    - GDAL/OGR
    - PyProj
    - Cartopy
    - Rasterio
    - Geoplot
    - Basemap
    - Bokeh
    - PySAL
    - Spatial Pandas
    - NetworkX
    - PyShp
    - TileStache
    - GdalUtils
    - Scipy
    - PyTopo
    - Geopy
    - Plotly

??? exemple "Conda"

    DAaaS utilise *Artifactory* pour la gestion des packages et des bibliothèques :
    ```
    https://jfrog.aaw.cloud.statcan.ca/artifactory/conda-forge-remote
    ```

    **Pour utiliser :**

    Miniforge et l'artifactory conda ont déjà été ajoutés à votre chemin système.  
    **Vous ne devriez pas avoir besoin de spécifier le canal.**  
    Si cela échoue, nous avons inclus des exemples de connexions directes après les exemples simples :

    ```python
    conda install [package]
    ```

    Pour des versions spécifiques
    ```python
    conda install geopandas
    conda install matplotlib=3.7.0
    ```

    Connexion directe au canal artifactory :

    ```python
    conda install -c https://jfrog.aaw.cloud.statcan.ca/artifactory/conda-forge-remote/ [package]
    conda install -c https://jfrog.aaw.cloud.statcan.ca/artifactory/conda-forge-remote/ [package=X.X...]

    ```
    
    Confirmez l'installation de votre package
    ```python
    conda list
    ```
    
    ??? exemple "Feuille de triche Conda"
        ![Feuille de triche Conda](imagesFR/conda-cheatsheeta.png)

        **Lien vers la [feuille de triche Conda complète](https://docs.conda.io/projects/conda/en/4.6.0/_downloads/52a95608c49671267e40c689e0bc00ca/conda-cheatsheet.pdf)**

??? exemple "PIP"
	PIP a également été préconfiguré pour utiliser l'index personnalisé DAS artifactory :

    ```python
    pip install [package] 
    ```


    ```python
    pip list
    ```

	Si cela échoue et que vous devez spécifier l'url de l'index :
	```python
	pip install --index-url https://jfrog.aaw.cloud.statcan.ca/artifactory/api/pypi/pypi-remote/simple <package-name>
	```

##Quelques exemples de base

??? quote "Se connecter à GAE ArcGIS Portal (Enterprise)"
    Votre groupe de projet vous fournira un ID client lors de l'intégration, qui sera utilisé pour vous connecter au portail ArcGIS Enterprise. Collez l'ID client entre les guillemets
    ```python
    from arcgis.gis import GIS
    gis = GIS("https://geoanalyticsdev.cloud.statcan.ca/portal", client_id=' ')
    print("Connexion réussie en tant que : " + gis.properties.user.username)
    ```
    Cela déclenchera une fenêtre contextuelle pour l'authentification, puis vous fournira une clé à entrer dans l'IDE

??? quote "Convertir un WFS en DataFrame pandas"
    ```python
    import geopandas as gpd

    # Définir l'URL WFS et le nom de la couche
    wfs_url = 'https://mywfs.com/wfs'
    layer_name = 'my_layer'

    # Lire le WFS dans un dataframe GeoPandas
    gdf = gpd.read_file(wfs_url, layer=layer_name)

    # Convertir le dataframe GeoPandas en dataframe pandas
    df = gdf.drop(columns='geometry')

    # Aperçu du dataframe
    print(df.head())
    ```

	
??? quote "Shapefile vers GeoDataFrame (Spatial DataFrame)"
    ```python
    import geopandas as gpd

    # Définir le chemin d'accès vers le shapefile
    shapefile_path = 'chemin/vers/votre/fichier_shape.shp'

    # Utiliser geopandas pour lire le shapefile dans un GeoDataFrame
    gdf = gpd.read_file(shapefile_path)

    # Afficher le GeoDataFrame
    print(gdf)
    ```

??? quote "Exporter un GeoDataFrame vers ArcGIS Enterprise"
    ```python
    from arcgis.gis import GIS
    import geopandas as gpd

    # Définir l'URL de votre portail ArcGIS Enterprise
    portal_url = 'https://geoanalytics.cloud.statcan.ca/portal/'

    # Créer une connexion à votre portail
    gis = GIS(portal_url, client_id='')

    # Définir le nom de la couche d'entités à créer
    layer_name = 'votre_nom_de_couche'

    # Publier le GeoDataFrame sur votre portail en tant que couche d'entités
    feature_layer = gis.content.import_data(gdf, title=layer_name)

    # Afficher l'URL de la couche d'entités
    print(feature_layer.url)
    ```

??? quote "Joindre CSV à SHP (en tant que sdf) puis exporter vers ArcGIS Enterprise"
    ```python
    import pandas as pd
    from arcgis.gis import GIS
    from arcgis.features import SpatialDataFrame

    # Charger le fichier CSV dans un dataframe Pandas
    csv_df = pd.read_csv('chemin/vers/fichier_csv.csv')

    # Charger les données spatiales dans un SpatialDataFrame en utilisant l'API ArcGIS for Python
    sdf = SpatialDataFrame.from_featureclass('chemin/vers/données_spatiales.shp')

    # Joindre le dataframe CSV au dataframe spatial en utilisant un champ commun
    joined_sdf = sdf.merge(csv_df, on='champ_commun')

    # Exporter le SpatialDataFrame joint vers ArcGIS Enterprise en utilisant l'API ArcGIS for Python
    gis = GIS('https://geoanalytics.cloud.statcan.ca/portal/', client_id='')
    joined_fc = joined_sdf.spatial.to_featureclass(location='chemin/vers/sortie.gdb', overwrite=True)
    joined_item = gis.content.add({'type': 'Feature Service', 'title': 'Données Jointes', 'tags': 'Data'}, data=joined_fc)
    joined_item.publish()
    ```
    Ce code charge d'abord un fichier CSV dans un dataframe Pandas en utilisant la fonction pd.read_csv(). Ensuite, il charge un ensemble de données spatiales dans un SpatialDataFrame en utilisant la méthode SpatialDataFrame.from_featureclass() de l'API ArcGIS for Python. Les deux dataframes sont ensuite joints en fonction d'un champ commun à l'aide de la méthode merge() du SpatialDataFrame.

    Enfin, le SpatialDataFrame joint est exporté vers une classe d'entités en utilisant la méthode spatial.to_featureclass() du SpatialDataFrame, puis publié sur ArcGIS Enterprise en utilisant les méthodes gis.content.add() et publish() de l'API ArcGIS for Python. Notez que vous devrez remplacer les chemins d'exemple et l'URL du serveur par les chemins réels et l'URL de vos données et de votre instance d'ArcGIS Enterprise.



??? quote "Analyse de données matricielles avec GDAL"
    ```python
    from osgeo import gdal
    import numpy as np

    # Ouvrir le fichier raster
    raster_ds = gdal.Open('chemin/vers/raster.tif')

    # Lire la bande raster dans un tableau NumPy
    raster_band = raster_ds.GetRasterBand(1)
    raster_array = raster_band.ReadAsArray()

    # Effectuer une analyse sur les données raster
    # Par exemple, calculer la valeur moyenne des pixels
    mean_value = np.mean(raster_array)

    # Afficher le résultat
    print('Valeur moyenne du pixel : {}'.format(mean_value))
    ```
    Ce code ouvre un fichier raster en utilisant la méthode gdal.Open() et lit la première bande du raster dans un tableau NumPy en utilisant la méthode ReadAsArray() de l'objet gdal.Band. Ensuite, il effectue une analyse sur les données raster, dans ce cas en calculant la valeur moyenne des pixels en utilisant la fonction np.mean() de NumPy. Enfin, il affiche le résultat dans la console.

    Vous pouvez modifier ce code pour effectuer d'autres types d'analyses sur les données raster, comme calculer le minimum, le maximum ou l'écart type des valeurs des pixels, ou effectuer des calculs entre plusieurs bandes. GDAL offre une large gamme de fonctions et d'outils pour travailler avec des données raster, donc les possibilités sont presque infinies.

##En savoir plus
[En savoir plus sur Artifactory](https://statcan.github.io/cae-eac/fr/Artifactory/)

[En savoir plus sur Conda](https://conda.io/projects/conda/fr/latest/user-guide/tasks/manage-environments.html) (EN)
