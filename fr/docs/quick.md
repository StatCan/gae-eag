# Pour commencer

Cette page fournit une aide courte et résumée pour les questions fréquemment posées. Chaque bloc d'aide est lié à un guide plus détaillé pour obtenir des informations supplémentaires.

---

??? tip "Comment lancer votre machine virtuelle - Utilisateurs externes"
    1. Rendez-vous sur : [Portail DAS](https://www.statcan.gc.ca/data-analytics-services/gae)
    2. Connectez-vous avec votre compte *@ext.statcan.ca*
    3. Faites défiler vers le bas de la page, sélectionnez votre machine virtuelle
    4. Sur la page Azure qui s'ouvre, démarrez votre machine virtuelle, puis utilisez "Browser Connect" (connexion via le navigateur)
    5. Entrez vos informations d'identification, votre machine virtuelle s'ouvrira dans un nouvel onglet (assurez-vous d'autoriser les fenêtres contextuelles)

??? tip "Comment lancer votre machine virtuelle - Employés de StatCan"
    ??? success "Prérequis"
        Vous avez déjà réclamé votre machine virtuelle

    **Aide complète :
    [Lien vers la page d'aide sur les machines virtuelles](/vm/#start-your-virtual-machine)**

    **Aide rapide :**
    
    1. Accédez au Portail Azure : *https://portal.azure.com/#home*
    2. Sélectionnez "Plus de services" et recherchez : DevTest Labs
    3. Assurez-vous que "Subscription Equals" est défini sur "ALL"
    4. Sélectionnez "geop-prod-intuser-dtl"
    5. Localisez et sélectionnez votre machine virtuelle
    6. Sélectionnez "Start" (Démarrer), attendez la confirmation, sélectionnez "Browser Connect" (connexion via le navigateur)
    7. :bangbang: N'oubliez pas de **STOPPER** votre machine virtuelle lorsque vous avez terminé :bangbang:

??? info "Accéder à l'interface du portail ArcGIS Enterprise"
    **Aide complète :
    [Lien vers la page d'aide du portail ArcGIS Enterprise](/arcgisportal/)**

    **Aide rapide :**

    1. Accédez via cette URL : [Portail d'entreprise DAS GEA](https://geoanalytics.cloud.statcan.ca/portal/home/)
    2. Cliquez sur "StatCan Azure Cloud Login" (Connexion au cloud Azure de StatCan)
    3. Si c'est votre première visite, vous devrez effectuer quelques étapes d'inscription, puis contactez le DAS GEA pour configurer votre compte

??? info "Se connecter au portail ArcGIS Enterprise de GAE via une API"
    Votre groupe de projet recevra un ID client lors de l'intégration, qui sera utilisé pour se connecter au portail ArcGIS Enterprise. Collez l'ID client entre les guillemets
    ```python
    from arcgis.gis import GIS
    gis = GIS("https://geoanalyticsdev.cloud.statcan.ca/portal", client_id=' ')
    
    # Cela déclenchera une fenêtre contextuelle pour l'authentification, puis vous fournira une clé à saisir dans l'EDI

    print("Connecté avec succès en tant que : " + gis.properties.user.username)
    ```

??? example "Comment accéder à votre base de données"
    **Aide complète :
    [Lien vers la page d'aide PostgreSQL+PostGIS](/postgresql/)**

    **Dans ArcPro**

    1. Dans le volet Catalogue, cliquez avec le bouton droit sur **Databases** (Bases de données) et sélectionnez **Add Database** (Ajouter une base de données)
        
    2. Dans la nouvelle fenêtre, développez **This PC** (Cet ordinateur) et localisez votre partage de fichiers de projet (monté en tant que lecteur), sélectionnez le fichier **.sde**

    <hr>
    **Dans QGIS**
    
    1. Dans l'onglet navigateur, cliquez avec le bouton droit sur **PostgreSQL** et sélectionnez **New Connection** (Nouvelle connexion)

    2. Entrez les informations suivantes :
        - **Name** (Nom) = nom choisi (alias) pour la base de données
        - **Host** (Hôte) = instance de la base de données *voir le partage de fichiers du projet*
        - **Port** = 5432
        - **Database** (Base de données) = le véritable nom du schéma *voir le partage de fichiers du projet*
        - **SSL mode** (Mode SSL) = allow (autoriser)
        - **Authentication** (Authentification) = *Appuyez sur le bouton vert +, puis *voir le partage de fichiers du projet*
        - **Also list tables with no geometry** (Lister également les tables sans géométrie) = YES (OUI)
        
    3. Sélectionnez **Test Connection** (Tester la connexion)

    <hr>
    **Avec Python**
    ```python
        import psycopg2

        conn = psycopg2.connect(
            dbname="votre_nom_de_base_de_données",
            user="votre_nom_utilisateur",
            password="votre_mot_de_passe",
            host="votre_hôte",
            port=5432
        )
        
        query = "SELECT * FROM votre_table;"
        
        conn.close()
    ```

??? example "Comment accéder à votre Field Filer (utilisateurs internes)"
    **Aide complète :
    [Lien vers la page d'aide complète](/filers/)**

    1. Ouvrez l'explorateur de fichiers Windows

    2. Collez le chemin du Field Filer dans la barre d'adresse **ET ajoutez .statcan.ca au chemin**
    > Exemple :  \\\filer03.statcan.ca

    3. Authentifiez-vous
        Nom d'utilisateur : ** Ajoutez stc\ ** avant votre nom d'utilisateur
    > Exemple : ** stc\nomutilisateur **
    4. Localisez le dossier racine, cliquez avec le bouton droit, sélectionnez "Map Network Drive" (Mapper un lecteur réseau)
        
??? question "Comment contacter le DAS GAE"
    **Aide complète :
    [Lien vers la page de contact](/contact)**

    **Aide rapide :**
    
    Email : statcan.dassupport-soutiendelads.statcan@statcan.gc.ca

    Pour les employés de StatCan, veuillez soumettre une demande via Jira :

    1. Ouvrez le logiciel de support de Statistique Canada Jira : [DAS Geospatial Environment (DASGAE)](https://jirab.statcan.ca/projects/DASGEO/summary)
    2. Dans la barre de menu, sélectionnez le bouton "Create" (Créer) :
    3. Dans la fenêtre de création de demande Jira, sélectionnez le type de demande = "Client Support" (Assistance client) :
    4. Dans la fenêtre de création de demande Jira, saisissez les informations relatives à votre demande

??? success "Liens utiles du DAS"
    [Portail ArcGIS Enterprise DAS GAE](https://geoanalytics.cloud.statcan.ca/portal/home/)

    [Environnement analytique collaboratif](https://www.statcan.gc.ca/data-analytics-services/cae)

    [Guide d'auto-assistance CAE](https://statcan.github.io/cae-eac/en/)

    [Espace de travail pour l'analyse avancée](https://www.statcan.gc.ca/data-analytics-services/aaw)

    [Guide d'auto-assistance AAW](https://statcan.github.io/aaw)

    [Aide du portail ArcGIS Enterprise d'ESRI](https://enterprise.arcgis.com/fr/portal/latest/use/what-is-portal-for-arcgis-.htm)

    [Documents d'aide Azure](https://docs.microsoft.com/fr/azure/?product=popular)

    [Documents d'aide QGIS](https://docs.qgis.org/3.22/fr/docs/user_manual/index.html)

    [Plateforme géospatiale fédérale](https://gcgeo.gc.ca/)

    <hr style="height:1px; background-color:green">

    **Acronymes et termes du DAS**
    
    |Terme||Description/Signification|
    |----||----|
    |DAS||Services d'analyse des données|
    |GAE||Environnement d'analyse géospatial|
    |AAW||Espace de travail pour l'analyse avancée [lien]|
    |CAE||Environnement analytique créatif [lien]|
    |FAIR(FDI)||**F**indable, **A**ccessible, **I**nteroperable, **R**eusable (trouvable, accessible, interopérable, réutilisable) ; Infrastructure et pipelines de données|
    |Jira||Logiciel de suivi et de gestion des tickets de support à StatCan|
    |VM||Machine virtuelle(s)|
    |GPU||Unité de traitement graphique ; VM GEA|
    |AVD||Bureau virtuel Azure|
    |2(M)FA||Authentification à deux facteurs ou plus|
    |Azure ID||Connexion cloud StatCan ; prenom.nom@cloud.statcan.ca|
