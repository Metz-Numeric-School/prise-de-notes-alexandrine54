

### Contexte et objectif 


Maîtriser les fonctions avancées du système d’exploitation Windows sur les postes clients d’une entreprise


- Installer, optimiser et dépanner les postes sous Windows dans un environnement réseau
- Déployer des postes de travail sous Windows
- Analyser les performances d’un poste de travail sous Windows
- Être capable de protéger et récupérer un système Windows
### Introduction au Déploiement de Windows


Le déploiement de Windows est une opération essentielle dans les entreprises, particulièrement celles qui gèrent un grand nombre de postes de travail.

Au lieu d’installer un système d’exploitation manuellement sur chaque poste, les administrateurs peuvent automatiser cette tâche grâce à des outils et des méthodes de déploiement.


Cela permet de gagner du temps (donc réduire les coûts), d’assurer une cohérence des configurations, et de réduire les erreurs humaines.


### Contexte d'utilisation 

- Renouvellement d'un parc informatique
- Ajout de nouveaux postes
- Réinstallation après une cyberattaque ou un dysfonctionnement critique

### Méthode de déploiement


Il existe plusieurs approches pour déployer Windows en entreprise, chacune adaptée à
des besoins spécifiques. Voici les principales :

1. Installation Manuelle :
→ Adaptée pour des besoins ponctuels
→ Longue et sujette à des erreurs humaines
→ Pas scalable pour une entreprise

2. Clonage de systèmes :
→ Création d'une image d'un système Windows configuré (modèle)
→ Déploiement rapide sur plusieurs machines
→ Limité aux configurations matérielles similaires


3. Déploiement automatisé :

→ Utilisation de fichiers de réponses (unattend.xml)
→ Automatisation complète du processus d'installation
→ Idéal pour les parcs informatiques hétérogènes

4. Déploiement centralisé :
→ Basé sur des serveurs tels que Windows Deployment Services ou SCCM
→ Gestion des installations via le réseau
→ Convient aux grandes entreprises avec des parcs informatiques importants


### Outils Principaux pour le Déploiement

→ Microsoft propose une série d’outils intégrés et complémentaires pour le déploiement
de Windows. Voici les principaux :

→ Windows PE (WinPE)
→ DISM
→ Unattend.xml
→ Sysprep
→ ADK



### ADK

Windows ADK (Assessment and Deployment Kit) appelé en français Kit de déploiement
et d’évaluation Windows, est une suite d'outils et de technologies conçue par Microsoft
pour faciliter la personnalisation, l'évaluation et le déploiement des systèmes d'exploitation
Windows sur des ordinateurs.


### Windows PE (WinPE)


WinPE est un mini-système d’exploitation conçu par Microsoft. Il est utilisé pour installer,
déployer et dépanner Windows. Il s'exécute directement depuis une clé USB ou un CD,
sans nécessiter d’installation sur le disque dur.


### Dism 

DISM (Deployment Image Servicing and Management) est un outil en ligne de
commande pour manipuler les fichiers WIM. Il permet de :
• Capturer une image d’un système Windows
• Modifier une image pour ajouter ou supprimer une fonctionnalité
• Déployer une image sur une nouvelle machine

### Unattend.xml


C’est un fichier de réponses XML utilisé pour automatiser l’installation de Windows en répondant aux invites utilisateur pendant le processus d’installation

Les 4 paramètres principaux :

1. WindowsPE : Configure les paramètres initiaux, comme la partition de disque
2. OfflineServicing : Ajoute des mises à jour et pilotes pendant l’installation hors ligne
3. Specialize : Configure les paramètres réseau et de domaine
4. OOBE (Out-of-Box Experience) : Définit les paramètres utilisateur, comme le compte administrateur et le fuseau horaire

### Sysprep


Avant de pouvoir déployer une image Windows sur de nouveaux PC, vous devez d’abord
généraliser cette image. La généralisation de l’image supprime les informations spécifiques à
l’ordinateur, telles que les pilotes installés et l’identificateur de sécurité (SID) de l’ordinateur.

Vous pouvez utiliser Sysprep seul ou Sysprep avec un fichier de réponses Unattend.xml pour généraliser votre image et la préparer au déploiement.

## Création d’une clé de Boot

###  Windows PE
    
Windows Preinstallation Environment (WinPE) est un mini-système d’exploitation conçu par Microsoft. Il est utilisé pour installer, déployer et dépanner Windows. Il s'exécute directement depuis une clé USB ou un CD, sans nécessiter d’installation sur le disque dur.
    
Caractéristiques de WinPE
    
Caractéristiques principales :
    
- Fournit un environnement temporaire pour préparer une machine
-  Permet de capturer ou déployer des images système
-  Inclut des outils pour diagnostiquer et réparer des systèmes Windows
    
    Cas d’utilisation :
    
-  Pré-installation de Windows sur des machines neuves
-  Clonage et déploiement d'images système
- Récupération de données ou réparation après une panne critique
    
    Mais il est aussi possible de :
    
    - Configurer votre disque dur avant d’installer Windows.
    - Installer Windows à l’aide d’applications ou de scripts à partir d’un réseau ou d’un lecteur local.
    - Capturer et appliquer des images Windows.
    - Modifier le système d’exploitation Windows lorsqu’il n’est pas en cours d’exécution.
    - Configurer des outils de récupération automatique.
    - Récupérer des données à partir d’appareils non démarrables.
    - Ajoutez votre propre interpréteur de commandes ou votre interface graphique personnalisée pour automatiser ce type de tâches.
    
    ## Commandes utiles sur WinPE
    
    **diskpart** : Permet de gérer les partitions de disque **wmic** : Fournit des informations système sur le matériel **dism** : Sert à gérer les images Windows **notepad** : Ouvre un éditeur de texte **regedit** : Lance d’éditeur de registre **ver** : Connaitre la version du système nouveau .

    
   ### 3. Clonage et gestion d’image
    
    ## Introduction au clonage
    
    Le clonage consiste à dupliquer un système d’exploitation et ses configurations pour les reproduire sur plusieurs machines. Cela permet un gain de temps considérable dans les environnements d’entreprise où des déploiements à grande échelle sont nécessaires Avantages du clonage :
    
    - Réduction du temps d’installation et de configuration
    - Uniformité des environnements de travail
    - Simplification des mises à jour ou migrations
    
    ## Le format WIM
    
    Windows Imaging Format Format d’image utilisé par Microsoft pour capturer, modifier et déployer des systèmes d’exploitation Permet de stocker plusieurs images dans un seul fichier (par exemple, différentes éditions de Windows). Offre une compression efficace pour économiser de l’espace disque


### 5. Synthèse Déploiement d’image

### Synthèse

- Le déploiement automatisé de Windows est un pilier essentiel pour gérer efficacement les parcs

informatiques en entreprise.

- Plusieurs méthodes de déploiement existent, chacune adaptée à des besoins spécifiques.
- Microsoft fournit des outils puissants comme WinPE, DISM et SYSPREP pour simplifier le processus.
- WinPE est un outil essentiel pour déployer et dépanner Windows.
- La création d'une clé USB bootable est une compétence fondamentale pour les administrateurs
- Les outils ADK, DiskPart, et à exécuter les commandes nécessaires.
- Le clonage permet d’accélérer le déploiement et d’uniformiser les configurations.
- Le format WIM est flexible et efficace pour stocker plusieurs images
- Les fichiers unattend.xml permettent une installation entièrement automatisée et personnalisée de Windows.
- SYSPREP est essentiel pour la préparation d’images généralisées avant le déploiement.
- La combinaison des deux outils offre une solution puissante pour les environnements professionnels.
- DISM est un outil puissant pour gérer et déployer des images Windows dans des environnements professionnels.
- La capture et le déploiement d’images standardisées améliorent l’efficacité et réduisent les erreurs.
- La maîtrise de DISM est essentielle pour les administrateurs système travaillant avec Windows.



