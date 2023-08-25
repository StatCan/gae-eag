# Options de stockage

## Aperçu des options de stockage

Lorsque vous travaillez avec vos données spatiales, vous avez plusieurs options de stockage parmi lesquelles choisir. Chaque option a ses propres caractéristiques et avantages.

1. **ArcGIS** <br>
ArcGIS offre une solution complète de stockage pour vos données spatiales. Il propose une géodatabase, qui est un conteneur permettant d'organiser et de gérer vos données géographiques, y compris les classes d'entités, les tables et les relations. De plus, ArcGIS vous permet d'enregistrer votre schéma PostgreSQL en tant que couches dans le portail, ce qui vous permet de diffuser les données et de créer des applications.

2. **PostgreSQL + PostGIS** <br>
PostgreSQL, associé à l'extension PostGIS, offre une puissante solution de base de données open source pour les données spatiales. Il offre des capacités spatiales avancées, vous permettant de stocker et d'interroger efficacement des données géospatiales. Avec l'extension PostGIS, vous pouvez effectuer des opérations et des analyses spatiales directement dans la base de données. PostgreSQL + PostGIS est un choix populaire pour les organisations recherchant une base de données spatiale robuste et évolutive.

3. **Azure Blob** <br>
Azure Blob Storage est un service de stockage d'objets basé sur le cloud fourni par Microsoft Azure. Il convient pour stocker de grandes quantités de données non structurées, y compris des fichiers et des documents. Azure Blob offre une grande évolutivité, une durabilité et une disponibilité élevées, ce qui en fait une option fiable pour la gestion et l'accès à vos données non géospatiales. Si vous avez des données géospatiales stockées dans Azure Blob, les utilisateurs devront utiliser Azure Storage Explorer pour copier les données localement afin de les accéder.

4. **Field Filers** <br>
Pour les utilisateurs internes (employés de Statistique Canada), les Field Filers offrent un moyen pratique de stocker et de partager des fichiers dans le cadre de votre projet. Ils fournissent une approche simple et conviviale pour la gestion collaborative des fichiers. Les Field Filers peuvent être montés sur votre DAS VM pour une utilisation facilitée.

Chaque option de stockage a ses propres avantages et considérations. En fonction de vos besoins spécifiques et de vos flux de travail, DAS peut vous aider à choisir l'option qui convient le mieux à vos besoins.



## ArcGIS vs PostgreSQL

| Cas d'utilisation | ArcGIS Datastore | PostgreSQL (avec PostGIS) |
|---|---|---|
| Intégration avec la plateforme ArcGIS | Intégration transparente avec les composants ArcGIS | Intégration avec une configuration et une installation supplémentaires (enregistrement du datastore) |
| Simplicité et facilité de configuration | Déploiement et gestion simplifiés (convivialité de l'utilisateur) | Nécessite des connaissances et une certaine expertise technique pour la personnalisation |
| Collaboration et partage | Fonctionnalités de collaboration natives au sein de la plateforme ArcGIS | Permet une édition collaborative des données géospatiales ; partage limité |
| Optimisation des performances pour les services ArcGIS | Optimisé pour la diffusion des données vers les services ArcGIS | L'optimisation des performances peut nécessiter des ajustements supplémentaires |
| Analyse spatiale et requêtes avancées | Interopérabilité avec ArcGIS Pro | Capacités spatiales avancées et requêtes basées sur SQL |
| Personnalisation et contrôle sur la base de données |   | Gestion flexible de la base de données avec des fonctionnalités spatiales supplémentaires |
| Intégration avec des systèmes et des applications externes | Intégration via l'API REST ou Python | Intégration avec divers systèmes et outils externes |

L'utilisation d'une base de données PostgreSQL (avec ou sans enregistrement de couches ArcGIS) est recommandée lorsque vous avez des exigences spécifiques ou des préférences pour la gestion et l'accès à vos données géospatiales. Cela offre plus de flexibilité et de contrôle sur le stockage de vos données et vous permet de tirer parti des fonctionnalités avancées de PostgreSQL, telles que les extensions spatiales comme PostGIS pour effectuer des analyses spatiales avancées, y compris l'acheminement. De plus, l'utilisation d'une base de données PostgreSQL vous permet de vous intégrer à d'autres applications et systèmes qui interagissent directement avec la base de données.

D'autre part, l'utilisation d'ArcGIS Server en tant que datastore est adaptée lorsque vous préférez une solution rationalisée et intégrée dans l'écosystème ArcGIS, avec une gestion simplifiée des données et une administration via les outils et les flux de travail d'ArcGIS.

En fin de compte, la meilleure approche dépend de votre projet spécifique, des exigences de vos données, des besoins d'intégration et des préférences de votre organisation. Il est recommandé d'évaluer ces facteurs et de consulter les experts de DAS-GAE et de la base de données informatique pour déterminer l'approche la plus adaptée à votre situation.


---

!!!warning
	Il incombe à l'utilisateur de s'assurer que les données entrantes ont été approuvées par l'OPMIC. 