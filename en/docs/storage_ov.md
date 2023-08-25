# Storage Options

## Storage Options Overview

When working with your spatial data, you have several storage options to choose from. Each option has its own characteristics and benefits.

1. **ArcGIS** <br>
ArcGIS provides a comprehensive storage solution for your spatial data. It offers a geodatabase, which is a container for organizing and managing your geographic data, including feature classes, tables, and relationships. Additionally, ArcGIS allows you to register your PostgreSQL schema as layers in the portal, enabling you to serve the data and build apps. 

2. **PostgreSQL + PostGIS ** <br>
PostgreSQL, together with the PostGIS extension, offers a powerful **open-source database solution** for spatial data. It provides advanced spatial capabilities, allowing you to store and query geospatial data efficiently. With the PostGIS extension, you can perform spatial operations and analyses directly within the database. PostgreSQL + PostGIS is a popular choice for organizations seeking a robust and scalable spatial database.

3. **Azure Blob** <br>
Azure Blob storage is a cloud-based object storage service provided by Microsoft Azure. It is suitable for storing large amounts of unstructured data, including files and documents. Azure Blob provides high scalability, durability, and availability, making it a reliable option for managing and accessing your non-geospatial data.  If you have geospatial data stored in Azure Blob, users will need to utilize Azure Storage Explorer to copy the data locally in order to access it.

4. **Field Filers** <br>
For internal users (Stat-Can Employees) Field Filers, offer a convenient way to store and share files within your project. They provide a simple and user-friendly approach for collaborative file management. Field Filers can be mounted to your DAS VM for ease-of-use.

Each storage option has its own advantages and considerations. Depending on your specific requirements and workflows, DAS can help choose the option that best suits your needs.


## ArcGIS vs PostgreSQL

| Use Case| ArcGIS Datastore | PostgreSQL (with PostGIS)|
|---|---|---|
|Integration with the ArcGIS platform| Seamless integration with ArcGIS components| Integration with additional configuration and setup (registering datastore)|
|Simplicity and ease of setup| Simplified deployment and management (user friendly)| Requires knowledge and some technical expertise for customization|
|Collaboration and sharing| Native collaboration features within ArcGIS platform| Allows for collaborative editing of geospatial data; limited sharing|
|Performance optimization for ArcGIS services| Optimized for serving data to ArcGIS services| Performance optimization may require additional fine-tuning|
|Advanced spatial analysis and querying| Interoperability with ArcGIS Pro | Advanced spatial capabilities and SQL-based querying|
|Customization and control over the database|   | Flexible database management with additional spatial functionality|
|Integration with external systems and applications| Integration via REST or Python API| Integration with various external systems and tools|

Using a PostgreSQL database (with or without) registered ArcGIS layers is recommended when you have specific requirements or preferences for managing and accessing your geospatial data. It offers more flexibility and control over your data storage and allows you to leverage the advanced capabilities of PostgreSQL, such as spatial extensions like PostGIS for performing advanced spatial analysis, including routing. Additionally, using a PostgreSQL database allows you to integrate with other applications and systems that interact directly with the database. 

On the other hand, using ArcGIS Server as a datastore is suitable when you prefer a streamlined and integrated solution within the ArcGIS ecosystem, with simplified data management and administration through ArcGIS tools and workflows.

Ultimately, the best approach depends on your specific project, data requirements, integration needs, and organizational preferences. It is recommended to evaluate these factors and consult with DAS-GAE and IT database experts to determine the most suitable approach for your situation.

---

!!!warning
	It is up to the user to ensure that incoming data has been OPMIC approved. 