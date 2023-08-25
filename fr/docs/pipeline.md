!!! bug "Cette page est incomplète"
	Plus d'informations et de services à venir !

# Azure Blobs

Les blobs sont gérés et maintenus par l'équipe DAS-FDI, garantissant la disponibilité et la fiabilité de l'infrastructure de stockage sur l'ensemble de la plateforme DAS et AVD.

Azure Blobs est un service de stockage cloud évolutif et rentable pour les données non structurées, offrant durabilité, disponibilité et sécurité. Il offre une intégration transparente avec d'autres services Azure pour la création d'applications robustes. Bien qu'Azure Blobs soit principalement conçu pour les données non structurées, il peut également être utilisé pour stocker et gérer des données géospatiales, même si les données géospatiales sont généralement structurées.

Lors de la manipulation de données géospatiales stockées dans Azure Blob, les utilisateurs disposent de plusieurs options pour une collaboration efficace. Ils peuvent soit copier les données localement à l'aide d'Azure Data Explorer pour une utilisation individuelle, soit utiliser Azure Data Explorer pour copier les données, puis les charger dans le portail ArcGIS ou une base de données PostgreSQL pour un travail collaboratif. Ces approches garantissent une accessibilité fluide aux données et permettent une collaboration efficace entre les membres de l'équipe.


### Utilisation d'Azure Data Explorer

1. Lancez Azure Storage Explorer et connectez-vous si nécessaire à votre compte.

2. Connectez-vous à votre stockage Azure Blob en sélectionnant le conteneur dans la barre de menu de gauche (ou en effectuant une recherche).

3. Une fois connecté, vous verrez les conteneurs Blob et leur contenu dans l'interface Azure Storage Explorer.

4. Pour copier des données localement, accédez au conteneur Blob souhaité, sélectionnez les fichiers ou dossiers que vous souhaitez copier, et choisissez l'option "Télécharger".

5. Pour télécharger des données vers le stockage Blob, sélectionnez le conteneur Blob de destination, choisissez l'option "Téléverser" et sélectionnez les fichiers ou dossiers que vous souhaitez téléverser.

6. Azure Storage Explorer propose également des fonctionnalités de renommage, de suppression et de gestion des conteneurs Blob et de leurs propriétés.
