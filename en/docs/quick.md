# Getting Started

This page provides short, summarized help for common FAQs. Each help block links to a more detailed guide for further information.

---

??? tip "How to launch your VM - External Users"
	1. Visit: [DAS Portal](https://www.statcan.gc.ca/data-analytics-services/gae)
	2. Sign in using your *@ext.statcan.ca* account
	3. Scroll down to the bottom of the page, select your VM
	4. In the Azure page which opens, Start your VM, then use 'Browser Connect'
	5. Enter your credentials, your VM will open in a new tab (ensure pop-ups are allowed)

??? tip "How to launch your VM - StatCan Employees"	
	??? success "Prerequisites"
		You have already claimed your VM 
		
	**Full Help:
	[Link to VM Help Page](/vm/#start-your-virtual-machine)**

	**Quick Help:**
	
	1. Access the Azure Portal: *https://portal.azure.com/#home*
	2. Select More Services and search for: DevTest Labs
	3. Ensure *Subscription Equals* is set to *ALL*
	4. Select *geop-prod-intuser-dtl*
	5. Locate and Select your VM
	6. Select *Start*, wait for confirmation, Select *Browser Connect*
	7. :bangbang: Remember to **STOP** your VM when finished :bangbang:


??? info "Acccess ArcGIS Enterprise Portal Interface"
	**Full Help:
	[Link to Help ArcGIS Enterprise Portal Page](/arcgisPortal/)**

	**Quick Help:**

	1. Access via this URL: [DAS GEA Enterprise Portal](https://geoanalytics.cloud.statcan.ca/portal/home/)
	2. Click the *StatCan Azure Cloud Login*
	3. If this is your first time accessing it, you will have to do some registration steps, then contact DAS GEA to have your account configured

??? info "Connect to GAE ArcGIS Enterprise Portal via API"
	Your project group will be provided with a Client ID upon onboarding which will be used to connect to the ArcGIS Enterprise Portal. Paste the Client ID in-between the quotations
	```python
	from arcgis.gis import GIS
	gis = GIS("https://geoanalyticsdev.cloud.statcan.ca/portal", client_id=' ')
	
	#This will trigger a pop-up window  to authenticate, then provide you with a key to enter into the IDE

	print("Successfully logged in as: " + gis.properties.user.username)
	```

??? example "How to access your Database"
	**Full Help:
	[Link to PostgreSQL+PostGIS Help Page](/postgresql/)**
	

	**In ArcPro** 
	
	1. In the Catalog pane, right-click **Databases** and select **Add Database**
		
	2. In the new window, expand **This PC** and located your project File-share (mounted as a drive), select the **.sde file**

	<hr>
	**In QGIS**
	
	1. Under the browser tab, Right-click **PostgreSQL**, and select **New Connection**

	2. Enter the following information:
		- **Name** = chosen name(alias) for the database
		- **Host** = Database Instance *see project file-share*
		- **Port** = 5432
		- **Database** = The true name of the schema *see project file-share*
		- **SSL mode** = allow
		- **Authentication** = *Press the green + button, then *see project file-share*
		- **Also list tables with no geometry** = YES 
		
	3. Select **Test Connection**
	
	<hr>
	**With python**
	```python
		import psycopg2

		conn = psycopg2.connect(
			dbname="your_database_name",
			user="your_username",
			password="your_password",
			host="your_host",
			port=5432
		)
		
		query = "SELECT * FROM your_table;
		
		conn.close()

	```
<!------
I have no clue why, but for the next block 'field filers'; in order to have two \\ in the example for step 2, you need to put three \\\ in the md file
----->

??? example "How to access your Field Filer (Internal users)"
	**Full Help:
	[Link to Full Help page](/filers/)**
	
	1. Open Windows File Explorer

	2. Paste FieldFiler path into the address bar **AND append .statcan.ca to the path**
	> example:  \\\filer03.statcan.ca

	3. Authenticate
		Username: ** Add stc\ ** before your username
	> example: ** stc\namenick **
	4. Locate the root folder, right click, Map Network Drive
		
		
??? question "How to contact DAS GAE"
	**Full Help:
	[Link to Contact Help Page](/contact)**

	**Quick Help:**
	
	Email: statcan.dassupport-soutiendelads.statcan@statcan.gc.ca

	For StatCan Employees, please submit a ticket via Jira:

	1. Open Statistics Canada Jira software: [DAS Geospatial Environment (DASGAE)](https://jirab.statcan.ca/projects/DASGEO/summary)
	2. From the Menu Bar, select the button “Create”:
	3. In the Jira Create Issue Window, Select the Issue Type = “Client Support”:
	4. In the Jira Create Issue window, enter the information related to your request

??? success "Useful DAS Links"
	[DAS GAE ArcGIS Portal](https://geoanalytics.cloud.statcan.ca/portal/home/)

	<hr style="height:0.5px">

	[Collaborative Analytics Environment]()

	[CAE Self-Help Guidebook](https://statcan.github.io/cae-eac/en/)

	<hr style="height:0.5px">

	[Advanced Analytics Workspace](https://analytics-platform.statcan.gc.ca/covid19)

	[AAW Self-Help Guidebook](https://statcan.github.io/daaas/en/)

	<hr style="height:0.5px">

	[ESRI ArcGIS Enterprise Portal Help](https://enterprise.arcgis.com/en/portal/latest/use/what-is-portal-for-arcgis-.htm)

	[Azure Help Documents](https://docs.microsoft.com/en-us/azure/?product=popular)

	[QGIS Help Documents](https://docs.qgis.org/3.22/en/docs/user_manual/index.html)

	[Federal Geospatial Platform](https://gcgeo.gc.ca/)

	<hr style="height:1px; background-color:green">

	**DAS Acronyms & Terms**
	
	|Term||Description/Meaning|
	|----||----|
	|DAS||Data Analytics Services|
	|GAE||Geospatial Analytic Environment|
	|AAW||Advanced Analytics Workspace [link]|
	|CAE||Creative Analytic Environment [link]|
	|FAIR(FDI)||**F**indable, **A**ccessible, **I**nteroperable, **R**eusable; Data Infrastructure & Pipelines|
	|Jira||Support ticketing and tracking software in STC|
	|VM||Virtual Machine(s)|
	|GPU|| Graphics processing unit; GEA VMs|
	|AVD||Azure Virtual Desktop|
	|2(M)FA||Two+ factor authentication|
	|Azure ID||StatCan Cloud login; first.last@cloud.statcan.ca|