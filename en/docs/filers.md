!!! warning "This feature is for Internal Users (StatCan Employees) Only." 


#Mounting Field Filers as a Drive

To mount a Field Filer to your DAS VM do the following:

1. Open Windows File Explorer

2. Paste FieldFiler path into the address bar **AND append .statcan.ca to the path**
	
	>\\\filer03 becomes... ** \\\filer03.statcan.ca **

3. Authenticate
	Username: ** Add stc\ ** before your username
	
	>example: ** stc\namenick **
	
	>Password: your ** NetB/OZ ** passcode

4. Locate the root folder you are interested in, right click, Map Network Drive
	This will mount it as a drive, allowing for direct connections via ArcGIS Pro
	
??? tip "Network Lag - When to copy locally"
	Field filers provide a means to transfer data over the cloud network. In cases where there is network lag or it is deemed more efficient, it is recommended to copy the data locally, perform the analysis, and subsequently save the results back to the filer. 
	
	This approach ensures smoother data handling and processing, while reducing network burden and cloud costs. Field filers works best for analysis if the data is shared in the *Hot* tier, as this tier is optimized for transactions.