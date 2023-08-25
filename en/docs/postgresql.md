#  PostgreSQL+PostGIS &nbsp;&nbsp;&nbsp;&nbsp; ![postgis logo](images/postgresql/post.png)

??? success "Prerequisites"
	1. An onboarded project with a requested database 	
	2. A **virtual machine** in the DAaaS Environment with **pgAdmin** and/or **ArcGIS Pro** and/or **QGIS** and/or **CAE Azure Services**. See the [VM page](vm.md) for more information

## Accessing your Database:

??? example "1. pgAdmin"
	This is one of the more common tool for PostgreSQL database administration. PG-Admin has been installed on your VM.

	1. Connect to your cloud VM and launch **pgAdmin**.
		![LaunchPgAdmin](images/postgresql/PgSql_01.png)

	2. Add the server you need to connect to by right clicking on Servers in the top left corner
		![CreateServer](images/postgresql/PgSql_02.png)

	3. In the General tab, enter a name for your server. You can write the real name of the server
	   In the Connection tab, enter the full Server name and add your Cloud Account  as Username followed by the server name
	   or the active directory group you belong to followed by the server name if access to the server was granted to that active directory group.
		![pgAdminParameters](images/postgresql/PgSql_03.png)

	4. You can now see in the list of server the newly added server. 
	   Click on it to connect and you will be asked to enter a password
		![EnterPassword](images/postgresql/PgSql_04.png)

	Learn More: [pgAdmin docs](https://www.pgadmin.org/docs/pgadmin4/latest/getting_started.html)

??? example "2. ArcPro"
	GAE has streamlined the ArcGIS Pro-PostgreSQL connection process by utilizing a *.sde* file connection.

	1. In the Catalog pane, right-click *Databases* and select *Add Database*
	![propost1](images/pro/propost1.PNG)

	2. In the new window, expand *This PC* and located your project File share (mounted as a drive)
	![propost2](images/pro/propost2.PNG)

	3. Select the *.sde* file, and click *Ok*
	
	4. The PostgreSQL database will not appear under *Databases* in the *Catalog* pane.

	Learn More: [ArcGIS Pro Documentation](https://pro.arcgis.com/en/pro-app/2.8/help/data/databases/connect-postgresql.htm)

??? example "3. QGIS"
	1. Under the browser tab, Right-click PostgreSQL, and select *New Connection*

		![post_gis1](images/postgresql/post_qgis1.PNG)

	2. A new window will open:

		![post_gis2](images/postgresql/post_gis2.PNG)

	3. Enter the following information:

		|Field||Entry|
		|---||---|
		|Name||Your chosen name(alias) for the database|
		|Host||Database Instance *see onboarding info*|
		|Port||5432|
		|Database||The true name of the database *see project file-share; postgreqsl_connection.txt* |
		|SSL mode||allow|
		|Authentication||*Press the green + button, then enter your cloud info|
		|Also list tables with no geometry||YES|
		**All other fields can be left blank

	4. Select *Test Connection*

	5. The database will now appear under the *PostgreSQL* heading in the QGIS Browser

	Learn More:

	- [QGIS Documentation](https://docs.qgis.org/testing/en/docs/user_manual/managing_data_source/opening_data.html#creating-a-stored-connection)

	- [QGIS + Azure Documentation](https://techcommunity.microsoft.com/t5/azure-database-for-postgresql/qgis-azure-database-for-postgresql-postgis/ba-p/1152249)

	- [Line 45- Using QGIS with PostGIS: A Dynamic Duo (whitepaper - English only)](https://www.line-45.com/post/using-qgis-postgis-dynamic-duo)

??? example "4. CAE- Azure Cloud Services"
	**Azure Data Factory, Azure Data Bricks, Azure Synapse**

	[Learn how to use CAE services](https://statcan.github.io/cae-eac/en/PostgreSQL/)

	Please contact the support team through the https://cae-eac.slack.com channel if you need assistance.
	
??? example "5. Python"
	Replace the placeholders with your own database details to connect to your own PostgreSQL database.

		```
		import psycopg2

		conn = psycopg2.connect(
			dbname="your_database_name",
			user="your_username",
			password="your_password",
			host="your_host",
			port=5432
		)

		# Define the SQL query to select data from the table
		query = "SELECT * FROM your_table;"

		# Use pandas to read the query results into a dataframe
		df = pd.read_sql_query(query, conn)

		# Close the database connection
		conn.close()

		# Print the dataframe
		print(df)
		```

  
<hr style="height:1px; background-color:green">
##How to add data into your database

??? example "1. Python"
	There are many python packages available for working with PostgreSQL (SQLAlchemy, psycopg*, ogr2ogr...)  This example uses sqlalchemy with help from geoPandas to load a shapefile into the database:

		```
		import geopandas as gpd
		from sqlalchemy import create_engine

		# create the sqlalchemy connection engine
		# replace the < >
		#Example: "postgresql://myUsername:myPassword@geopostgresqlflex.postgres.database.azure.com:5432/myDataBase"
		db_connection_url = "postgresql://<username>:<password>@<instance>:<port>/<database>"
		link = create_engine(db_connection_url)

		# read in the data into a geo-dataframe
		gdf = gpd.read_file(r'path_to_file')

		# Push the geo-dataframe to postgresql
		gdf.to_postgis("<table_name>", link, index=False, if_exists='replace') 
		```
	---
	
		```
		import psycopg2
		from sqlalchemy import create_engine
		import pandas as pd

		# Connect to the database
		conn = psycopg2.connect(
			host="your_host",
			database="your_database",
			user="your_username",
			password="your_password"
		)

		# Create a SQLAlchemy engine to connect to the database
		engine = create_engine('postgresql://your_username:your_password@your_host/your_database')

		# Define the name of the table to be created in the database
		table_name = 'your_table'

		# Define the dataframe to be exported
		df = pd.DataFrame()

		# Use the to_sql method of the dataframe to export it to the database
		df.to_sql(table_name, engine, if_exists='replace')

		# Close the database connection
		conn.close()
		```	
	---
	
	Learn More:

	- [SQLAlchemy Docs](https://docs.sqlalchemy.org/en/14/)

	- [PYSHEET - SQLAlchemy cheatsheet (unofficial)](https://www.pythonsheets.com/notes/python-sqlalchemy.html)

	- [GeoPandas Docs](https://geopandas.org/en/stable/)
	
??? example "2. pgAdmim"
	pgAdmin Help Docs: [Import/Export Data](https://www.pgadmin.org/docs/pgadmin4/development/import_export_data.html)

	![Import/Export_postgresql](images/postgresql/PGimport_export_options.png)

??? example "3. QGIS"
	In current versions of QGIS you can export shape files to PostGIS using the build in DB Manager.  Somewhat counterintuitively, QGIS refers to this as 'importing to Postgis'. 

	1. Open DB Manager
	![open_DB](images/qgis/GZor3.jpg)

	2. In the list of PostGIS databases find the one you want to export to, find the desired schema and press import button (marked with the red outline).
	![layer_to_post](images/qgis/RAHSN.png)

	3. Choose the shape file in 'input' (must be in your 'Layers Panel') and press 'ok'
	![shp_to_post](images/qgis/4UuEs.png)

	Learn More: 

	- [QGIS Docs- Lesson: Import and Export](https://docs.qgis.org/3.22/en/docs/training_manual/spatial_databases/import_export.html#db-manager)

	- [OSGeo Docs- PostGIS Quick start](https://live.osgeo.org/en/quickstart/postgis_quickstart.html)

	- [Line 45- Using QGIS with PostGIS: A Dynamic Duo (whitepaper)](https://www.line-45.com/post/using-qgis-postgis-dynamic-duo)

??? example "4. ArcPro"
	To simplify the process, GAE has crated a database connection file for your project; .sde file.  This can be located in your project's file share which is mounted as a drive to your VM.
	
	1. When ready import your data into the PostgreSQL DB from arc pro, use the *Feature Class to Feature Class* tool.
	![pro to post](images/pro/propost1.PNG)
	
	2. For *Output Location* select the .sde file in your projects file share.
	![pro to post2](images/pro/propost2.PNG)
	
	3. *Output Name* will be the table name in the database
	
	4. Select run

---

##Tips

??? tip "Best Practices"
	-	Optimize your database: Use the appropriate indexes, and partition your data to improve performance.

	-	Use projections and coordinate systems: Always use the correct projection and coordinate system for your data. PostGIS provides functions for transforming between coordinate systems and projections.

	-	Keep your database clean: Regularly clean up your database by vacuuming, analyzing, and deleting unnecessary data.

	-	Use transactions: Use transactions to ensure that your database operations are atomic and consistent. This can prevent data corruption and improve performance.

	-	Use a backup strategy: Create and maintain regular backups of your database to prevent data loss.

	-	Document your database: Document your database schema, data structures, and other important details to ensure that others can understand and use your database.

---
??? tip "Learn more about PostgreSQL + PostGIS"
	Learn More: [About PostgreSQL](https://www.postgresql.org/)
	
	Learn More: [About PostGIS](https://postgis.net/)
	
	