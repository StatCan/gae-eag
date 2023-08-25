# Une brève introduction aux SIG

<p align='center'>
<img src="https://i.ibb.co/TrGQv9f/intro.png" alt="image HTML">
</p>

__L'analyse géospatiale concerne la localisation quantitative de caractéristiques importantes, appelées phénomènes.__

Les données géospatiales sont des données sur des phénomènes qui ont une localisation sur la surface de la Terre. La localisation peut être statique (par exemple, l'emplacement d'une route, un événement catastrophe, des citoyens vivant dans la pauvreté) ou dynamique (par exemple, un véhicule ou un piéton en mouvement, la propagation de la COVID).

Un SIG (Système d'Information Géospatial) nous aide à analyser les relations spatiales et les schémas entre ces phénomènes. Il est particulièrement utile pour visualiser les données spatiales et rapporter les résultats de l'analyse.

Les SIG sont composés à la fois de composants matériels et logiciels. En raison des grands volumes de données spatiales et de la nécessité d'afficher les valeurs en temps réel, le matériel des SIG dispose souvent de grandes capacités de stockage, d'une grande vitesse de calcul et d'une mémoire puissante. <b>DAS-GAE a été conçu pour répondre aux besoins de ces utilisateurs.</b>


---

## Pourquoi l'analyse géospatiale est-elle importante ?

L'analyse géospatiale est réalisée pour :

- Identifier des schémas et des relations spatiales dans les données.
- Soutenir la prise de décision dans des domaines tels que l'urbanisme, la gestion des catastrophes et l'environnement.
- Optimiser l'allocation et la gestion des ressources.
- Évaluer et atténuer les risques liés aux catastrophes naturelles et aux urgences de santé publique.
- Surveiller et analyser les changements et les impacts environnementaux.

---

## Données spatiales

Les données spatiales font référence aux informations qui ont une composante de localisation ou géographique associée. Ce sont des **données qui ont une référence spatiale, comme la latitude et la longitude ou une adresse**, ce qui leur permet d'être affichées sur une carte et analysées à l'aide d'un logiciel de système d'information géographique (SIG). Les données spatiales peuvent être largement classées en deux types : les données vectorielles et les données raster.

1. **Données vectorielles** : Les données vectorielles représentent des caractéristiques géographiques à l'aide de points, de lignes et de polygones. Des exemples de données vectorielles incluent :
   - **Points** : adresses, villes, aéroports, hôpitaux et autres emplacements discrets.
   - **Lignes** : routes, rivières, chemins de fer et autres caractéristiques linéaires.
   - **Polygones** : pays, états, comtés, parcs et autres zones avec des limites bien définies.

2. **Données raster** : Les données raster représentent des caractéristiques géographiques sous la forme d'une grille de cellules, où chaque cellule a une valeur qui représente un aspect de la caractéristique représentée. Des exemples de données raster incluent :
   - Données d'élévation : modèles numériques d'élévation (MNE) et modèles numériques de terrain (MNT).
   - Imagerie satellite : photographies aériennes, imagerie multispectrale et imagerie thermique.
   - Données climatiques : température, précipitations et autres données météorologiques.

Les données vectorielles et raster peuvent être utilisées dans une large gamme d'applications SIG, telles que l'analyse spatiale, la cartographie et la modélisation environnementale.

Une **base de données spatiale** - également appelée "géodatabase" - est conçue pour capturer et stocker les points, les lignes et les polygones.

Une géodatabase est un type de base de données utilisé pour stocker et gérer des données géospatiales, y compris des entités, des attributs et des relations. Elle est conçue pour prendre en charge le stockage, la requête et la manipulation de données géographiques de manière à préserver les relations spatiales et temporelles entre les entités. Une géodatabase peut stocker différents types de données, notamment des points, des lignes, des polygones et des jeux de données raster, et peut être utilisée pour une large gamme d'applications, notamment l'analyse SIG, la production de cartes et la gestion des données. Les géodatabases sont généralement créées et gérées à l'aide de logiciels spécialisés, tels que ArcGIS d'Esri.


## Analyse géospatiale
### Méthodes courantes
- **Interrogation spatiale** : Recherche et récupération de données basées sur des critères spatiaux spécifiques ou des relations spatiales.

- **Statistiques spatiales** : Analyse des schémas, des distributions et des relations au sein des données spatiales en utilisant des techniques statistiques.

- **Modélisation spatiale** : Création de modèles mathématiques ou informatiques pour simuler et prédire des phénomènes ou des processus spatiaux.

- **Interpolation spatiale** : Estimation des valeurs dans des emplacements non observés en se basant sur des valeurs connues des emplacements voisins.

- **Géocodage** : Conversion d'adresses ou de noms de lieux en coordonnées géographiques (latitude et longitude).

- **Analyse de réseau** : Examen de la connectivité, du flux et de l'accessibilité au sein d'un réseau, tel que les réseaux de transport ou les réseaux de services publics.

- **Télédétection** : Analyse de données acquises à partir de satellites, d'aéronefs ou d'autres capteurs pour étudier et surveiller la surface de la Terre.

- **Géostatistique** : Application de méthodes statistiques pour analyser et modéliser la variabilité spatiale et l'incertitude dans les données.

- **Visualisation spatiale** : Représentation des données géospatiales à travers des cartes, des graphiques et d'autres formats visuels pour faciliter la compréhension et la communication.

Ces méthodes sont généralement utilisées en combinaison, en fonction des objectifs spécifiques de l'analyse et des caractéristiques des données étudiées.


### Projections et Coordonnées
Comprendre les projections et les systèmes de coordonnées est essentiel en SIG pour assurer une représentation et une analyse précises des données spatiales. En sélectionnant la bonne projection, en tenant compte de l'objectif de la carte et en gérant efficacement les distorsions, les utilisateurs de SIG peuvent travailler avec des données spatiales de manière précise et significative.

#### Projections
Les projections cartographiques sont nécessaires car la surface courbe de la Terre ne peut pas être parfaitement représentée sur une carte plane. Cela introduit des distorsions de forme, de superficie, de distance et de direction. Aucune projection ne peut éliminer simultanément toutes les distorsions, il est donc nécessaire de choisir une projection appropriée en fonction de l'objectif de la carte et des propriétés à maintenir ou à minimiser.

Il est essentiel de s'assurer que tous les ensembles de données et les couches sont dans la même projection pour une analyse géospatiale précise et significative, car cela permet un alignement correct, une cohérence de mesure et des relations spatiales valides entre différentes entités géographiques.

Dans ArcGIS, vous pouvez modifier ou reprojeter des données en utilisant l'outil "Projet", qui vous permet de convertir des données d'un système de coordonnées à un autre.

Dans QGIS, vous pouvez modifier ou reprojeter des données en utilisant l'outil "Reprojeter la couche", qui vous permet de transformer des données d'un système de coordonnées à un autre.

En Python, vous pouvez effectuer la reprojection de données géospatiales en utilisant diverses bibliothèques telles que pyproj et gdal.

Projections couramment utilisées :

**Projection de Mercator** : La projection de Mercator est largement utilisée pour les cartes du monde, les cartes de navigation et les applications de cartographie en ligne. ArcGIS/ESRI a adopté une version modifiée de la projection de Mercator appelée "Web Mercator Auxiliary Sphere" (WGS 1984 Web Mercator, ou Web Mercator abrégé) comme projection par défaut pour les services de cartographie Web au sein de leur écosystème logiciel.

**Projection conique conforme de Lambert** : La projection personnalisée utilisée par Statistique Canada est une variante de la projection conique conforme de Lambert. La projection de Lambert de Statistique Canada est spécifiquement basée sur la projection conique conforme de Lambert, qui est un type de projection conique connue pour préserver les angles et les formes locaux.

#### Systèmes de coordonnées
Les systèmes de coordonnées fournissent un cadre de référence pour définir des emplacements sur la surface de la Terre. Il existe deux principaux types : les systèmes de coordonnées géographiques (latitude et longitude) et les systèmes de coordonnées projetées (coordonnées X et Y sur une carte plane).
Les systèmes de coordonnées géographiques sont sphériques et mesurent les positions en latitude et longitude.
Les systèmes de coordonnées projetées utilisent des coordonnées cartésiennes et sont utilisés pour des mesures et des analyses précises.

## GIS Vocabulary

| Terme | | Description |
|-------|---|-------------|
| API | | Interface de programmation d'application - une méthode permettant aux développeurs de logiciels de permettre la communication entre différentes applications ou systèmes. |
| ArcGIS | | Suite de logiciels de système d'information géographique (SIG) développée par ESRI. |
| ArcGIS Pro | | Une application SIG de bureau dans la suite ArcGIS pour une analyse géospatiale avancée, la gestion des données et la visualisation. |
| Application (App) | | Abréviation de "application", faisant référence à un logiciel conçu pour s'exécuter sur des PCs, smartphones, des tablettes ou d'autres appareils. |
| Attribut (Attribute) | | Informations non spatiales associées à des données géospatiales, stockées dans des tables attributaires. |
| Carte de base (Basemap) | | Données SIG et/ou imagerie qui constituent le contexte d'arrière-plan d'une carte. |
| Tampon (Buffer) | | Zone ou région créée autour d'une entité géographique, souvent utilisée pour des analyses de proximité. |
| Cartographie (Cartography) | | L'art et la science de créer des cartes, y compris la conception, la symbolisation et la production de cartes. |
| Carte choroplèthe (Choropleth Map) | | Une carte thématique qui utilise des teintes ou des motifs différents pour représenter des valeurs de données pour des zones géographiques spécifiques. |
| Coordonnées (Coordinates) | | Valeurs représentées par les lettres x, y, z [ou m (mesure)], qui définissent une position dans une référence spatiale. |
| Système de Référence des Coordonnées (CRS) | | Système de référence des coordonnées - un cadre utilisé pour définir et localiser des entités géographiques sur la surface de la Terre. |
| DCAT, geoDCAT-ap | | Norme de métadonnées permettant de rendre les ensembles de données spatiales, les séries de données et les services consultables dans les catalogues de données générales. |
| Modèle Numérique d'Élévation (DEM) | | Une représentation numérique du relief ou de la topographie d'une surface. |
| Extraction, Transformation et Chargement (ETL) | | Procédure de copie de données à partir de sources vers un système de destination qui représente les données différemment de la source ou dans un contexte différent de celui de la source. |
| Généralisation (Generalization) | | Méthode utilisée dans les SIG pour réduire les détails dans les données (pour des raisons de confidentialité et/ou de visualisation). |
| Géocodage (Geocode) | | Le processus d'identification d'une localisation par un ou plusieurs attributs, généralement une adresse ou une latitude/longitude, à partir d'une couche. |
| Géodatabase (Geodatabase) | | Un conteneur ou un format de fichier utilisé pour stocker, gérer et organiser des données géospatiales de manière structurée. |
| Système d'Information Géographique (SIG) | | Un système conçu pour capturer, stocker, analyser, gérer et présenter des données spatiales et attributaires. |
| Géotraitement (Geoprocessing) | | L'analyse et la manipulation de données géospatiales à l'aide d'outils et d'algorithmes SIG. |
| Géospatial (Geospatial) | | Relatif à des données associées à un emplacement spécifique sur la surface de la Terre. |
| HNAP | | HNAP-Canada est un profil du profil harmonisé nord-américain qui est lui-même un profil du standard ISO19139 (ISO 19115*). |
| Environnement de Développement Intégré (IDE) | | Une application logicielle fournissant des outils complets pour le développement de logiciels. |
| Jupyter Notebook | | Une application Web open source qui permet aux utilisateurs de créer et de partager des documents contenant du code en direct, des équations, des visualisations et du texte narratif. |
| Couche (Layer) | | Données thématiques décrites et stockées dans une bibliothèque de cartes. Les couches agissent comme des transparences qui peuvent être superposées les unes aux autres pour la visualisation ou l'analyse spatiale. |
| Métadonnées (Metadata) | | Informations décrivant les caractéristiques et les propriétés des données géospatiales, telles que leur source, leur qualité et leur contenu. |
| OGC | | Open Geospatial Consortium - champion des logiciels Open Source et des normes ouvertes. |
| PostgreSQL | | Système de gestion de base de données objet-relationnel open source ; Azure Managed. |
| Projection | | Une transformation mathématique appliquée aux données spatiales pour les convertir de la surface courbe de la Terre à une surface plane, généralement une carte. |
| Python | | Un langage de programmation de haut niveau populaire largement utilisé dans l'analyse géospatiale et le scripting dans le domaine des SIG. |
| R | | Un langage de programmation et un environnement logiciel utilisés couramment dans l'analyse et la visualisation de données. |
| Raster | | Un format de données qui représente des informations géographiques sous forme de grille de cellules ou de pixels, couramment utilisé pour les images satellites et les données d'élévation. |
| Shapefile | | Format de stockage de données vectorielles permettant de stocker l'emplacement, la forme et les attributs. Il est stocké dans un ensemble de 4 fichiers connexes et contient une classe d'entités. *Les Shapefiles doivent être évités si possible*. |
| Topologie (Topology) | | Les relations spatiales et la connectivité entre les entités géométriques au sein d'un ensemble de données SIG. |
| Vecteur (Vector) | | Un format de données qui représente des entités géométriques telles que des points, des lignes ou des polygones dans un espace bidimensionnel ou tridimensionnel. |
| Web Map | | Une carte interactive accessible via Internet, souvent construite à l'aide de technologies web et de données géospatiales. |
| WFS | | Spécifications qui normalisent la manipulation de données et l'affichage de cartes sur Internet. |
| WMS | | Spécifications qui permettent un accès uniforme par les clients web à des cartes rendues par des serveurs de cartes sur Internet. |
