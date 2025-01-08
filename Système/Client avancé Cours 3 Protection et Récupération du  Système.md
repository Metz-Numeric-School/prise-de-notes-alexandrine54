
## 1 Réinitialisation et Historique des fichiers

**Objectif** : Comprendre comment utiliser les fonctionnalités natives de Windows pour réinitialiser un PC et gérer les sauvegardes grâce à l’historique des fichiers

## Fonctionnalité "Réinitialiser ce PC"
    
- Fonctionnalité intégrée à Windows pour résoudre les problèmes logiciels graves.
    - Remet le système à son état d'origine (usine) tout en offrant des options pour conserver les données.
    
    #### Options disponibles :
    
    - **Conserver mes fichiers :** Supprime les applications et paramètres mais garde les fichiers personnels. Usage : Si le système est lent ou instable.
    - **Tout supprimer :** Supprime tout, y compris les fichiers personnels. Usage : Préparation d’un PC avant cession ou revente
    
    #### Cas pratiques :
    
    - Résolution de logiciels malveillants
    - Restauration après une mise à jour défectueuse
    - Si le système est lent ou instable
    - Préparation d’un PC avant cession ou revente
    
    ## Fonctionnalité "Historique des Fichiers"
    
    Sauvegarde automatique des fichiers présents dans les bibliothèques, le bureau et les dossiers sélectionnés
    
    - **Sauvegarde incrémentale :** Conserve plusieurs versions d'un même fichier.
    - **Emplacement de stockage :** Disque dur externe, réseau
    
    ### Avantages et limites :
    
    #### Réinitialisation :
    
    - Simple à utiliser, intégrée à Windows
    - Ne résout pas les problèmes matériels
    
    #### Historique des fichiers :
    
    - Versionnage des fichiers, rapide à configurer
    - Nécessite un stockage externe
    


#### 2 Sauvegarde de Fichiers et Création de Points de Restauration


**Objectif** : Apprendre à configurer et utiliser les sauvegardes locales et les points de restauration pour protéger les systèmes Windows et récupérer les données en cas de problème.
 
## Pourquoi sauvegarder et créer des points de restauration ?
    
- Pannes matérielles, virus, ou erreurs humaines peuvent entraîner des pertes de données.
    - Les sauvegardes et points de restauration permettent une récupération rapide.
    
    ## Différences entre sauvegarde et points de restauration ?
    
    - **Sauvegarde :** Copies des fichiers ou du système à un moment précis.
    - **Point de restauration :** Snapshot du système (paramètres et registre) sans affecter les fichiers personnels.
    
    ## La sauvegarde
    
    La sauvegarde de données consiste à réaliser une copie des données qui ne sera pas accessible par les utilisateurs Cette copie n’est alors pas exposée aux changements et peut permettre de revenir en arrière après un changement non désiré Elle sert à rétablir un service avant une modification involontaire ou une panne matérielle Ne pas confondre avec le RAID qui lui permet la continuité de service Quand on utilise une sauvegarde pour revenir en arrière, on appelle cela une restauration La destination de sauvegarde s’appelle un support de sauvegarde Une sauvegarde pour être efficace doit respecter la règle des 3-2-1 :
    
    - 3 versions des données : Les données en tant que tel + 2 sauvegardes
    - 2 supports différents
    - 1 support hors site, si possible, déconnecté ou impossible à modifier
    
    Une sauvegarde pour être efficace doit être testée régulièrement :
    
    - Effectuer une vérification de la cohérence des fichiers de sauvegarde
    - Effectuer un test de restauration
    
    Une sauvegarde pour être efficace doit comporter plusieurs versions, ce qu’on appelle le temps de rétention

 Différents supports de sauvegarde
    
Une sauvegarde peut s’effectuer sur différents types de stockage :
    - Une disque dur externe ou une clé via l’interface USB
    - Un serveur de fichier ou un serveur NAS via le réseau
    - Des cartouches LTO (Linear Tape Open) ou RDX via un lecteur decartouches
    - Des stockages clouds dédiés à la sauvegarde via internet

Une solution très simple et économique est de combiner 2 disques dur externes à alterner régulièrement. Un sera stocké hors site.
    ### La sauvegarde locale
    
Les sauvegardes locales consistent à stocker les copies de sauvegarde sur des périphériques de stockage physiques situés sur site, tels que des disques durs externes, des serveurs de sauvegarde locaux ou des bandes magnétiques. #### Avantages :
    
 Contrôle total sur les données : Les données sont stockées et gérées localement, offrant un contrôle total sur la sécurité et la disponibilité des données.
    - Performances élevées : Les sauvegardes locales peuvent être plus rapides que les sauvegardes dans le cloud en raison de la vitesse des connexions locales.
#### Inconvénients :

- **Vulnérabilité aux sinistres locaux :** Les données sauvegardées localement peuvent être perdues en cas de sinistre local, tels qu'un incendie, un vol ou une catastrophe naturelle.    - **Coût de maintenance :** Les périphériques de stockage locaux nécessitent une maintenance régulière et peuvent entraîner des coûts supplémentaires pour les mises à niveau et le remplacement.

    ### La sauvegarde distante (et cloud)
    
    Les sauvegardes distantes consistent à stocker les copies de sauvegarde sur des périphériques de stockage physiques situés en dehors du site de l'entreprise, généralement dans un centre de données distant ou sur un site de sauvegarde tiers. (AWS, Microsoft Azure, Google Cloud Storage) #### Avantages :
    
    - **Protection contre les sinistres locaux :** Les sauvegardes distantes offrent une protection contre les sinistres locaux en assurant que les données sauvegardées sont stockées en dehors du site principal de l'entreprise.
    - **Redondance géographique :** Les sauvegardes distantes garantissent une redondance géographique des données, ce qui augmente la résilience et la disponibilité des données.
    
    #### Inconvénients :
    
    - **Dépendance à l'égard des connexions réseau :** Les sauvegardes distantes nécessitent une connexion réseau fiable et rapide, ce qui peut être un défi dans certaines situations.
    - **Coûts de bande passante :** Les sauvegardes distantes peuvent entraîner des coûts supplémentaires liés à l'utilisation de la bande passante pour transférer les données vers le site distant.
    
    → Une sauvegarde peut se faire de plusieurs manières :
    
    - Complète, qui consiste à réaliser une copie complète des données
    - Différentielle qui consiste à ne copier que les fichiers qui ont été modifié depuis la dernière sauvegarde complète
    - Incrémentielle qui consiste à ne copier que les fichiers qui ont été modifié depuis la dernière sauvegarde
    
    EXEMPLE DE RESTAURATION AVEC SAUVEGARDE INCREMENTIELLE
    
    ### La sauvegarde complète
    
    La sauvegarde complète consiste à copier intégralement toutes les données sélectionnées. Cela inclut tous les fichiers et répertoires, qu'ils aient été modifiés ou non depuis la dernière sauvegarde. Bien que cela nécessite souvent plus d'espace de stockage et de temps pour effectuer la sauvegarde, elle offre une simplicité et une fiabilité maximales lors de la restauration des données.
    
    - A chaque sauvegarde complète, l’intégralité des données sont à nouveau copiées sur le support de sauvegarde
    - Le temps de sauvegarde est long et proportionnel au volume de données à copier. La fréquence des sauvegardes est en général d’une semaine. Si les données changent très peu, il est alors possible d’espacer davantage les sauvegardes (1 fois par mois par exemple).
    - Pour restaurer les données il suffit de prendre la dernière sauvegarde complète.
    - Le temps de restauration est long et proportionnel au volume de données à copier.
    - Il n’est pas nécessaire de garder les sauvegardes les plus anciennes sauf obligation réglementaire comme la conservation des logs de navigation sur Internet pendant une année.

    
    ### La sauvegarde différentielle
    
    Il est d’abord nécessaire de réaliser une première sauvegarde complète. Puis les sauvegardes suivantes sont différentielles c’est à dire que le logiciel de sauvegarde vérifie quels sont les fichiers qui ont été modifiés depuis la sauvegarde complète. Toutes les sauvegardes différentielles suivantes se feront toujours par rapport à la première sauvegarde complète.
    
    - La sauvegarde différentielle est plus rapide et utilise moins d'espace de stockage. Cela est très utile pour des sauvegardes fréquentes et donc journalières. Le temps de sauvegarde prendra davantage de temps au fur et à mesure car la comparaison des fichiers s’effectue toujours par rapport à la toute première sauvegarde complète.
    - Seuls les fichiers modifiés depuis la sauvegarde complète sont sauvegardés.
    - La restauration nécessite uniquement la dernière sauvegarde complète ainsi que la dernière sauvegarde différentielle. Le temps de restauration va augmenter avec les sauvegardes différentielles successives et il est nécessaire de refaire une sauvegarde complète de temps en temps pour améliorer les durées d’exécution de restauration.
    
    
    ### La sauvegarde incrémentielle
    
    Il est d’abord nécessaire de réaliser une première sauvegarde complète. Puis les sauvegardes suivantes sont incrémentales c’est à dire que le logiciel de sauvegarde vérifie quels sont les fichiers qui ont été modifiés ou créés depuis la sauvegarde précédente, complète ou incrémentale. De cette manière, seuls les fichiers modifiés seront pris en compte dans cette sauvegarde incrémentale.
    
    - La sauvegarde incrémentale est très rapide et utilise un faible espace de stockage. Cela est très utile pour des sauvegardes fréquentes, journalières et même plusieurs fois par jour.
    - Seuls les fichiers modifiés sont sauvegardés.
    - La restauration est moins rapide car il est nécessaire d’utiliser la dernière sauvegarde complète ainsi que toutes les sauvegardes incrémentales réalisées depuis cette sauvegarde complète.
    
    #### Différentes technologies de sauvegarde Les outils de sauvegarde ont évolué avec le temps pour sauvegarder tout type de données :
    
    - Des machines virtuelles complètes
    - Des fichiers
    - Des bases de données
    - Etc.
    
    Afin de pouvoir copier un fichier ou un serveur en cours d’utilisation, la technologie de Shadow Copy est utilisée. Elle consiste à réaliser un instantané de la donnée à sauvegarder, et de sauvegarder cet instantané plutôt que le fichier réel Les outils de sauvegarde ont également accueilli avec le temps plusieurs fonctionnalités :
    
    - Compression et déduplication pour accélérer les temps de sauvegarde
    - La sauvegarde en mode « bloc » qui permet de lire les fichiers au niveau bloc. Cela est très performant en cas de sauvegarde incrémentielle où seront sauvegardé seulement les blocs modifiés de chaque fichier
    - Le chiffrage de la sauvegarde pour éviter un détournement des données
    - La vérification automatique de la cohérence des données
    - Le verrouillage des sauvegardes pour empêcher la corruption

    ### La sauvegarde de machine virtuelle
    
    La sauvegarde de machine virtuelle peut se faire manuellement en réalisant des exports. Cela reste coûteux en temps et en capacité de stockage Elle peut se faire en lançant une sauvegarde à l’intérieur de la machine virtuelle ou depuis l’hyperviseur en copiant les données Elle peut s’automatiser et profiter d’avantage via des logiciels de sauvegarde dédiées :
    
    - Sauvegarde de Windows serveur gratuit et intégré à Windows : Aussi bien en sauvegarde depuis l’hyperviseur que depuis la machine virtuelle
    - Veeam Backup & Replication : Optimisé pour la sauvegarde machine virtuelle; Compatible avec VMWare et Hyper-V; Gratuit jusqu’à 10 machines virtuelles
    - Etc.



### Magasin des Données de Configuration de Démarrage (BCD) et Windows RE


**Objectif :** Se familiariser avec les concepts avancés de gestion du démarrage Windows (BCD) et les outils de récupération disponibles dans Windows RE, pour assurer une continuité de fonctionnement après un problème.
    
## Qu'est ce que le BCD ?

Le BCD (Boot Configuration Data) est une base de données utilisée par Windows pour gérer les options de démarrage. Contient les informations nécessaires au démarrage du système, comme la localisation des fichiers système et les configurations associées. **Rôle :** Gérer plusieurs systèmes d’exploitation sur une même machine (dual boot). Modifier les paramètres de démarrage avancés. **Structure :** Organisé comme un registre avec des entrées pour chaque chargeur de démarrage. bcdedit /enum -> Affiche les entrées actuelles du BCD. bcdedit /set {ID} description « Nouveau nom » -> Change la description d’une entrée. bcdedit /delete {ID} -> Supprime une entrée du BCD. bcdedit /default {ID} -> Définit l’entrée par défaut pour le démarrage.
