# PostgreSQL+PostGIS &nbsp;&nbsp;&nbsp;&nbsp; ![postgis logo](imagesFR/postgresql/post.png)

??? success "Prérequis"
	1. Un projet intégré avec une base de données demandée
	2. Une **machine virtuelle** dans l'environnement DAaaS avec **pgAdmin** et/ou **ArcGIS Pro** et/ou **QGIS** et/ou **Services Azure CAE**. Voir la [page VM](vm.md) pour plus d'informations.

## Accéder à votre base de données :

??? example "1. pgAdmin"
	Il s'agit de l'un des outils les plus courants pour l'administration des bases de données PostgreSQL. PG-Admin est installé sur votre machine virtuelle.

	1. Connectez-vous à votre machine virtuelle dans le cloud et lancez **pgAdmin**.
	<!-- MISSINg	![LaunchPgAdmin](imagesFR/postgresql/PgSql_01.png) -->

	2. Ajoutez le serveur auquel vous souhaitez vous connecter en cliquant avec le bouton droit de la souris sur Servers dans le coin supérieur gauche.
		![CreateServer](imagesFR/postgresql/pgadmin1.PNG)

	3. Dans l'onglet General, donnez un nom à votre serveur. Vous pouvez utiliser le nom réel du serveur.
	   Dans l'onglet Connection, saisissez le nom complet du serveur et ajoutez votre compte Cloud en tant que nom d'utilisateur suivi du nom du serveur,
	   ou le groupe Active Directory auquel vous appartenez suivi du nom du serveur si l'accès au serveur a été accordé à ce groupe Active Directory.
		![pgAdminParameters](imagesFR/postgresql/pgadmin2.PNG)
		![pgAdminParameters](imagesFR/postgresql/pgadmin3.PNG)

	4. Vous pouvez maintenant voir le nouveau serveur ajouté dans la liste des serveurs.
	   Cliquez dessus pour vous connecter et vous serez invité à saisir un mot de passe.
		![EnterPassword](imagesFR/postgresql/pgadmin4.PNG)

	Apprenez-en davantage : [Documentation pgAdmin](https://www.pgadmin.org/docs/pgadmin4/latest/getting_started.html)

??? example "2. ArcPro"
	GAE a simplifié le processus de connexion ArcGIS Pro-PostgreSQL en utilisant un fichier de connexion *.sde*.

	1. Dans le volet Catalogue, cliquez avec le bouton droit sur *Databases* (Bases de données) et sélectionnez *Add Database* (Ajouter une base de données).
	![propost1](imagesFR/pro/propost1.PNG)

	2. Dans la nouvelle fenêtre, développez *This PC* (Ce PC) et localisez le partage de fichiers de votre projet (monté en tant que lecteur).
	![propost2](imagesFR/pro/propost2.PNG)

	3. Sélectionnez le fichier *.sde* et cliquez sur *Ok*.

	4. La base de données PostgreSQL apparaîtra maintenant sous *Databases* (Bases de données) dans le volet Catalogue.

	Apprenez-en davantage : [Documentation ArcGIS Pro](https://pro.arcgis.com/en/pro-app/2.8/help/data/databases/connect-postgresql.htm)

??? example "3. QGIS"
	1. Sous l'onglet Explorateur, cliquez avec le bouton droit sur PostgreSQL et sélectionnez *New Connection* (Nouvelle connexion).

		![post_gis1](imagesFR/postgresql/postq1.PNG)

	2. Une nouvelle fenêtre s'ouvrira :

		![post_gis2](imagesFR/postgresql/postq2.PNG)

	3. Entrez les informations suivantes :

		|Champ||Entrée|
		|---||---|
		|Name||Le nom choisi (alias) pour la base de données|
		|Host||Instance de la base de données *voir les informations d'intégration*|
		|Port||5432|
		|Database||Le véritable nom de la base de données *voir le partage de fichiers du projet ; postgreqsl_connection.txt*|
		|SSL mode||allow|
		|Authentication||*Appuyez sur le bouton vert +, puis saisissez vos informations Cloud|
		|Also list tables with no geometry||YES|
		**Tous les autres champs peuvent être laissés vides.

	4. Sélectionnez *Test Connection* (Tester la connexion).

	5. La base de données apparaîtra maintenant sous l'en-tête *PostgreSQL* dans le navigateur QGIS.

	Apprenez-en davantage :

	- [Documentation QGIS](https://docs.qgis.org/testing/en/docs/user_manual/managing_data_source/opening_data.html#creating-a-stored-connection)

	- [Documentation QGIS + Azure](https://techcommunity.microsoft.com/t5/azure-database-for-postgresql/qgis-azure-database-for-postgresql-postgis/ba-p/1152249)

	- [Ligne 45 - Utilisation de QGIS avec PostGIS: un duo dynamique (document technique - en anglais uniquement)](https://www.line-45.com/post/using-qgis-postgis-dynamic-duo)


??? example "4. CAE- Azure Cloud Services"
	**Azure Data Factory, Azure Data Bricks, Azure Synapse**

	[Apprenez à utiliser les services CAE](https://statcan.github.io/cae-eac/fr/PostgreSQL/)

	Veuillez contacter l'équipe de support via le canal https://cae-eac.slack.com si vous avez besoin d'aide.

??? example "5. Python"
	Remplacez les espaces réservés par les détails de votre propre base de données pour vous connecter à votre base de données PostgreSQL.

		```
		import psycopg2

		conn = psycopg2.connect(
			dbname="le_nom_de_votre_base_de_données",
			user="votre_nom_d'utilisateur",
			password="votre_mot_de_passe",
			host="votre_hôte",
			port=5432
		)

		# Définissez la requête SQL pour sélectionner des données dans la table
		query = "SELECT * FROM votre_table;"

		# Utilisez pandas pour lire les résultats de la requête dans un dataframe
		df = pd.read_sql_query(query, conn)

		# Fermez la connexion à la base de données
		conn.close()

		# Affichez le dataframe
		print(df)
		```

  
<hr style="height:1px; background-color:green">
##Comment ajouter des données dans votre base de données

??? example "1. Python"
	Il existe de nombreux packages Python disponibles pour travailler avec PostgreSQL (SQLAlchemy, psycopg*, ogr2ogr...). Cet exemple utilise SQLAlchemy avec l'aide de geoPandas pour charger un fichier shapefile dans la base de données :

		```
		import geopandas as gpd
		from sqlalchemy import create_engine

		# Créez la connexion SQLAlchemy avec la base de données
		# Remplacez les < >
		# Exemple : "postgresql://nomUtilisateur:monMotDePasse@geopostgresqlflex.postgres.database.azure.com:5432/maBaseDeDonnées"
		db_connection_url = "postgresql://<nom_utilisateur>:<mot_de_passe>@<instance>:<port>/<base_de_données>"
		link = create_engine(db_connection_url)

		# Lisez les données dans un géo-dataframe
		gdf = gpd.read_file(r'chemin_vers_le_fichier')

		# Poussez le géo-dataframe vers PostgreSQL
		gdf.to_postgis("<nom_table>", link, index=False, if_exists='replace') 
		```
	---
	
		```
		import psycopg2
		from sqlalchemy import create_engine
		import pandas as pd

		# Connectez-vous à la base de données
		conn = psycopg2.connect(
			host="votre_hôte",
			database="votre_base_de_données",
			user="votre_nom_d'utilisateur",
			password="votre_mot_de_passe"
		)

		# Créez un moteur SQLAlchemy pour vous connecter à la base de données
		engine = create_engine('postgresql://votre_nom_d_utilisateur:votre_mot_de_passe@votre_hôte/votre_base_de_données')

		# Définissez le nom de la table à créer dans la base de données
		table_name = 'votre_table'

		# Définissez le dataframe à exporter
		df = pd.DataFrame()

		# Utilisez la méthode to_sql du dataframe pour l'exporter vers la base de données
		df.to_sql(table_name, engine, if_exists='replace')

		# Fermez la connexion à la base de données
		conn.close()
		```	
	---
	
	Apprenez-en davantage :

	- [Documentation SQLAlchemy](https://docs.sqlalchemy.org/en/14/)

	- [PYSHEET - Feuille de triche SQLAlchemy (non officielle)](https://www.pythonsheets.com/notes/python-sqlalchemy.html)

	- [Documentation GeoPandas](https://geopandas.org/en/stable/)

	
??? example "2. pgAdmin"
	Documentation d'aide de pgAdmin : [Importer/Exporter des données](https://www.pgadmin.org/docs/pgadmin4/development/import_export_data.html)

	![Import/Export_postgresql](imagesFR/postgresql/PGimport_export_options.png)

??? example "3. QGIS"
	Dans les versions actuelles de QGIS, vous pouvez exporter des fichiers shape vers PostGIS en utilisant le gestionnaire de base de données intégré, appelé DB Manager. De manière quelque peu contre-intuitive, QGIS appelle cela "importer vers PostGIS".

	1. Ouvrez le DB Manager
	![open_DB](imagesFR/postgresql/postq3.PNG)

	2. Dans la liste des bases de données PostGIS, trouvez celle vers laquelle vous souhaitez exporter, trouvez le schéma souhaité et cliquez sur le bouton d'importation (marqué d'un contour rouge).
	![layer_to_post](imagesFR/postgresql/postq4.PNG)

	3. Choisissez le fichier shape dans la section 'input' (il doit être dans votre 'Layers Panel') et cliquez sur 'ok'.
	![shp_to_post](imagesFR/postgresql/postq5.PNG)

	Apprenez-en davantage :

	- [Documentation QGIS - Leçon : Importer et exporter](https://docs.qgis.org/3.22/en/docs/training_manual/spatial_databases/import_export.html#db-manager)

	- [Documentation OSGeo - PostGIS Quick start](https://live.osgeo.org/en/quickstart/postgis_quickstart.html)

	- [Line 45 - Utiliser QGIS avec PostGIS : un duo dynamique (whitepaper)](https://www.line-45.com/post/using-qgis-postgis-dynamic-duo)

??? example "4. ArcPro"
	Pour simplifier le processus, GAE a créé un fichier de connexion à la base de données pour votre projet ; le fichier .sde. Vous pouvez le trouver dans le partage de fichiers de votre projet, qui est monté comme un lecteur sur votre VM.
	
	1. Lorsque vous êtes prêt à importer vos données dans la base de données PostgreSQL depuis ArcGIS Pro, utilisez l'outil *Feature Class to Feature Class*.
	![pro to post](imagesFR/pro/propost1.PNG)
	
	2. Pour *Output Location*, sélectionnez le fichier .sde dans le partage de fichiers de votre projet.
	![pro to post2](imagesFR/pro/propost2.PNG)
	
	3. *Output Name* sera le nom de la table dans la base de données.
	
	4. Lancez l'opération.

---

##Conseils

??? tip "Bonnes pratiques"
	-	Optimisez votre base de données : Utilisez les index appropriés et partitionnez vos données pour améliorer les performances.

	-	Utilisez des projections et des systèmes de coordonnées : Utilisez toujours la projection et le système de coordonnées corrects pour vos données. PostGIS fournit des fonctions pour la transformation entre les systèmes de coordonnées et les projections.

	-	Maintenez votre base de données propre : Nettoyez régulièrement votre base de données en effectuant des opérations de vidange, d'analyse et de suppression des données inutiles.

	-	Utilisez des transactions : Utilisez des transactions pour garantir que vos opérations de base de données sont atomiques et cohérentes. Cela peut prévenir la corruption des données et améliorer les performances.

	-	Utilisez une stratégie de sauvegarde : Créez et maintenez des sauvegardes régulières de votre base de données pour prévenir la perte de données.

	-	Documentez votre base de données : Documentez le schéma de votre base de données, les structures de données et autres détails importants pour vous assurer que d'autres personnes peuvent comprendre et utiliser votre base de données.


---
??? tip "En savoir plus sur PostgreSQL + PostGIS"
	En savoir plus : [À propos de PostgreSQL](https://www.postgresql.org/)
	
	En savoir plus : [À propos de PostGIS](https://postgis.net/)

	
	