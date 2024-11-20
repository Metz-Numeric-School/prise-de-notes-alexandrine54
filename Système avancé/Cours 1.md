

#### 1 Analyse des ressources et des performances


##### Le gestionnaire des taches processus


![[Pasted image 20241120085517.png]]


![[Pasted image 20241120090605.png]] 



### L'analyseur de performances

-> L'analyse de performances permet d'affiner les recherches. Par exemple, dans le cas du processeur, des dizaines d'indicateurs sont possibles. Vous pouvez, entre autres, regarder le taux d'inactivité de votre processeur, mais aussi des moyennes.

-> Pour ajouter un indicateur à votre Analyseur de Performances, il vous suffit de :
- Cliquer sur le bouton + (vert)
- Sélectionner un compteur (c'est à dire un type : processeur, processus, RAM, etc...)
- Sélectionner une instance, ou plusieurs (c'est à dire un sous-type encore plus précis).

-> Dans notre cas, "Processus ", "% temps processeur" et ensuite le processus voulu


### Démarrage Sélectif 

-> Si l'une de vos applications ne fonctionne pas normalement, comme l'application métier de votre entreprise par exemple, il se peut que ce ne soit pas elle directement qui soit à mettre en cause mais plutôt la configuration de Windows. Autrement dit, ce qui est installé sur l'ordinateur et leurs paramètres.

-> Pour savoir si votre application est la cause du dysfonctionnement ou non, vous allez devoir redémarrer Windows en 'mode sélectif'. Ce mode vous permet de redémarrer Windows en ne sélectionnant que les services de base, et donc d'éliminer ceux qui seraient susceptibles de vous poser problème.



![[Pasted image 20241120092155.png]]

### Service

Pour rappel, un service n'est ni plus ni moins qu'un programme s'exéculant en arrière-plan.  
C'est-à-dire que vous ne le voyez pas forcément el qu'il ne dispose pas non plus d'interdace graphique montrant son exécution. Pour son fonctionnement, Windows lance une mulitude de services au démarrage. Beaucoup d'applications que vous installerez exécuteront un sevice sur votre ordinateur Windows. Il se peut qu'ils solent la cause d'un problème  
  
Si, au redémarrage de Windows, votre application fonctionne correctement, vous savez qu'il s'agit d'un problème lié à votre configuration. Il vous reste donc à trouver les modifications que vous avez effectuées sur votre ordinateur et qui empêchent votre application de fonctionner correctement. Dans le cas contraire, il ne vous reste plus qu'à contacter les développeurs de l'application.


#### Diagnostic de la mémoire vive 

PC qui plante, écran bleu, Ceci peut être dû à un problème de barrette mémoire. Ce
composant est souvent utilisé et très fragile, c'est pourquoi Windows propose un outil de diagnostic vous permettant de connaître l'état de votre RAM
Un autre outil plus puissant (mais non intégré à Windows) vous permet de tester votre mémoire vive en lui appliquant une série de tests (13 algorithmes de test de RAM différents sont disponibles). Il est beaucoup plus puissant et il est suivi et mis à jour régulièrement par son éditeur : MemTest86


#### Diagnostic de la mémoire vive Windows

→ Ouvrir « Diagnostic de mémoire Windows »
→ Deux choix s'offrent à vous : redémarrer tout de suite l'ordinateur afin d'effectuer le
diagnostic, ou effectuer le diagnostic au prochain redémarrage
→ Une fois sur l’écran du diagnostic, vous pouvez presser la touche F1 afin d’effectuer un test
approfondi
→ Choisissez « cache : actif » (il s’agit de la mémoire intégrée à votre CPU)
→ Choisissez la valeur cinq pour le nombre de passe (plus la panne est rare, plus il est difficile
de la trouver ; en faisant plusieurs passes, vous avez plus de chances de trouver la panne).


#### Diagnostic du disque dur

Les disques durs sont depuis plusieurs années équipés de systèmes SMART (Self-
Monitoring, Analysis, and Reporting Technology) qui vous permettent d'avoir des indications concernant leur état de santé. C'est important car, quand un disque dur tombe en panne, vous perdez généralement ses données.
Le principe est simple : chaque fois que le disque dur va rencontrer un problème, il ne va
pas vous le dire, mais il va mettre à jour sa liste d'incidents. On appelle ces informations les informations "SMART".

→ Voici quelques tests possibles pour les disques durs :
→ Avec WMIC (Windows Management Instrumentation Command-line)
”wmic diskdrive get status, model, size, mediatype”
cette méthode est ultra-simple mais aussi ultra-limitée
→ Pour avoir plus d’informations sur l’état de santé d’un disque dur, il faut se
tourner vers des logiciels tiers comme :
→ CrystalDiskInfo
→ Hard Disk Sentinel
→ HD Tune
→ Etc.

#### Medicat, l’outil magique !

Medicat, est un utilitaire bootable qui inclut une suite d’outils pour dépanner et analyser
un ordinateur facilement à la manière de Hiren’s Boot CD, mais beaucoup plus complet.

	• Utilitaires de récupérations de données

	• Live USB : Mini Windows 10
	
	• Outils de disques : Acronis Disk Director, DiskGenius, EaseUS Partition Master
	
	• Outils de sauvegarde et de récupération de fichiers

	• Outils de réparation du démarrage
	• Outils de diagnostics : Memtest86+, TestDisk

	• Analyses antivirus
	• Stress Test

	• Réinitialiser et suppression de mots de passe Windows



#### 3. Optimiser l’utilisation de votre ordinateur

##### Gestion des disques


→ Le « Gestionnaire de disque dur » est l'outil de Microsoft qui vous permet de gérer un
disque. Cet outil vous sera donc utile pour :
→ Ajouter un nouveau disque
→ Partitionner un disque dur, pour diviser un disque physique en plusieurs disques logiques
→ Formater un disque dur
→ Lors d'une réinstallation de Windows, cet outil vous sera présenté d'une façon un peu
différente mais les étapes resteront les mêmes. Vous aurez ainsi la possibilité de formater vos
disques durs à l’installation de Windows


##### Nettoyage des disques


Votre ordinateur doit être nettoyé comme on nettoie une pièce. Il faut que l'utilisateur range
ses fichiers dans les bons dossiers, tout comme nous rangeons nos affaires dans les placards, et qu’il supprime tout ce qui traîne, c'est-à-dire tout ce qui doit aller à la poubelle
Encore une fois, Windows met à votre disposition un outil vous permettant d'effectuer cette tâche.
Cet outil s'appelle « Nettoyage de disque ».
Son utilisation est très simple : il suffit de cocher les fichiers à supprimer et d’appuyer sur « OK


##### Automatiser une tache

→ Ouvrez un CMD et entrez la commande « cleanmgr /c /sageset:1 »
→ cleanmgr c’est donc le nettoyeur, /c vous permet de spécifier le disque (vous pouvez aussi choisir un autre disque), /sageset:1 va ouvrir le nettoyeur de disque, afin que vous puissiez cocher les dossiers que vous souhaitez nettoyer. Une fois fermé, le numéro 1 (vous pouvez en choisir un autre) aura retenu votre configuration
→ Entrez la commande « cleanmgr /c /sagerun:1 », /sagerun:1 va cette fois-ci lancer le nettoyeur de disque, avec les paramètres spécifiés correspondant au numéro 1, c'est-à-dire ce que vous avez
renseigné juste avant.

