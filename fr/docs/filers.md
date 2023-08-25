!!! warning "Cette fonctionnalité est réservée aux utilisateurs internes (employés de StatCan)."

# Montage des filers de terrain en tant que lecteur

Pour monter un filer de terrain sur votre machine virtuelle DAS, suivez les étapes suivantes :

1. Ouvrez l'Explorateur de fichiers Windows.

2. Collez le chemin du filer de terrain dans la barre d'adresse **ET ajoutez .statcan.ca au chemin**.

   > \\\filer03 devient... **\\\filer03.statcan.ca**

3. Authentifiez-vous.
   Nom d'utilisateur : ajoutez **stc\\** devant votre nom d'utilisateur.

   > Exemple : **stc\\namenick**

   Mot de passe : votre code d'accès **NetB/OZ**.

4. Localisez le dossier racine qui vous intéresse, faites un clic droit, puis sélectionnez "Connecter un lecteur réseau".
   Cela le montera en tant que lecteur, permettant des connexions directes via ArcGIS Pro.

??? tip "Latence du réseau - Quand copier localement"
   Les filers de terrain permettent de transférer des données via le réseau cloud. Dans les cas où il y a une latence du réseau ou où cela est jugé plus efficace, il est recommandé de copier les données localement, d'effectuer l'analyse, puis d'enregistrer les résultats sur le filer.

   Cette approche garantit une manipulation et un traitement des données plus fluides, tout en réduisant la charge du réseau et les coûts liés au cloud. Les filers de terrain fonctionnent mieux pour l'analyse si les données sont partagées dans le niveau *Hot*, car ce niveau est optimisé pour les transactions.
