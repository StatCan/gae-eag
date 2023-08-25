!!! bug "This page is incomplete"
	More information and services coming soon!

# Azure Blobs

Blobs are managed and maintained by the DAS-FDI team, ensuring the availability and reliability of the storage infrastructure across the entire DAS platform and AVD.

Azure Blobs is a scalable and cost-effective cloud storage service for unstructured data, offering durability, availability, and security. It provides seamless integration with other Azure services for building robust applications. While Azure Blobs is primarily designed for unstructured data, it can also be used for storing and managing geospatial data, even though geospatial data is typically structured.

When working with geospatial data stored in Azure Blob, users have a few options for efficient collaboration. They can either copy the data locally using Azure Data Explorer for individual use, or utilize Azure Data Explorer to copy the data and then load it into the ArcGIS portal or a PostgreSQL database for collaborative work. These approaches ensure smooth data accessibility and enable effective collaboration among team members.


### Using Azure Data Explorer

1. Launch Azure Storage Explorer and if necessary sign in to your account.

2. Connect to your Azure Blob storage by selecting the container from the left menu bar (or searching).

3. Once connected, you will see the Blob containers and their contents in the Azure Storage Explorer interface.

4. To copy data locally, navigate to the desired Blob container, select the files or folders you want to copy, and choose the "Download" option.

5. To upload data to Blob storage, select the destination Blob container, choose the "Upload" option, and select the files or folders you want to upload.

6. Azure Storage Explorer also provides features for renaming, deleting, and managing Blob containers and their properties.

