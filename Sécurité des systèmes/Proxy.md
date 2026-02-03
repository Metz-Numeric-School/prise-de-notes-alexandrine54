
Proxy = entre INTERNET et notre réseau local
Qu'est-ce-qu'un proxy ? 
Un **proxy** (litt. « mandataire ») est un [composant logiciel](https://fr.wikipedia.org/wiki/Composant_logiciel "Composant logiciel") [informatique](https://fr.wikipedia.org/wiki/Informatique "Informatique") qui joue le rôle d'intermédiaire en se plaçant entre deux hôtes pour faciliter ou surveiller leurs échanges.

Dans le cadre plus précis des [réseaux informatiques](https://fr.wikipedia.org/wiki/R%C3%A9seaux_informatiques "Réseaux informatiques"), un proxy est alors un programme servant d'intermédiaire pour accéder à un autre réseau, généralement [Internet](https://fr.wikipedia.org/wiki/Internet "Internet"). Par extension, on appelle aussi « proxy » un matériel comme un [serveur](https://fr.wikipedia.org/wiki/Serveur_informatique "Serveur informatique") mis en place pour assurer le fonctionnement de tels services.

Filezila = Est un programme ou « client » FTP (File Transfer Protocol) qui permet aux utilisateurs de déplacer des fichiers entre des ordinateurs en utilisant Internet**. Cela signifie que les gens utilisent FileZilla pour accomplir plusieurs tâches, telles que : Téléverser des fichiers. Télécharger des fichiers.

Les serveurs proxys sont notamment utilisés pour assurer les fonctions suivantes :

- accélération de la navigation : [mémoire cache](https://fr.wikipedia.org/wiki/M%C3%A9moire_cache "Mémoire cache"), [compression de données](https://fr.wikipedia.org/wiki/Compression_de_donn%C3%A9es "Compression de données") ;
- [historique](https://fr.wikipedia.org/wiki/Historique_\(informatique\) "Historique (informatique)") (logs) : journalisation des requêtes ;
- la sécurité du [réseau local](https://fr.wikipedia.org/wiki/R%C3%A9seau_local "Réseau local") ;
- le [filtrage](https://fr.wikipedia.org/wiki/Filtrage_d%27Internet "Filtrage d'Internet") : restrictions de sites, blocage des publicités ou des contenus lourds ([Java](https://fr.wikipedia.org/wiki/Java_\(langage\) "Java (langage)"), [Flash](https://fr.wikipedia.org/wiki/Adobe_Flash "Adobe Flash")) ;
- l'[anonymat](https://fr.wikipedia.org/wiki/Anonymat_sur_Internet "Anonymat sur Internet") ;
- la [répartition de charge](https://fr.wikipedia.org/wiki/R%C3%A9partition_de_charge "Répartition de charge") ;
### Créer une machine virtuelle 

écrire ces commande dans putty pour qu'on puisse installer l'iso de OpnSense dans le pnetlab

cd /opt/unetlab/addons/qemu/opnsense-24.7/  
  
/opt/qemu/bin/qemu-img create -f qcow2 virtioa.qcow2 10G  
  
cd  
  
/opt/unetlab/wrappers/unl_wrapper -a fixpermissions



Grace à ça on peut créer des vm dans des vm


Pour la VM : 4096 giga de rame minimum
Do not use a network
par default
20 giga minimum
Configuration de la vm :
Ajouter une carte réseau puis une 2ème
VMNET(0) NAT et un vmnet de notre choix (ne pas mettre sur le host-only)

Login : installer
password : opnsense

choisir : france accent
choisir installation ZFS

raid (stripe) = pas de redondance

on sélectionne notre disque dur avec espace
YES
exit and reboot
On va déconnecter le cdrom (dans cd(dvd))

On doit avoir 192.168.1.1 en LAN
Et en WAN, il faut avoir une IP sinon on doit inverser et lui assigner une IP
On va modifier l'adresse ip du LAN (option 1), non pas via le DHCP
exemple : 192.168.1.254 en /24
faire la touche entrée
faire NON
obtenir une adresse ipv6 = NON
Entrée
Activer le serveur dhcp sur le lan ? OUI
Donner l'étendue : 192.168.1.10, puis 192.168.1.20
Changer le certificat = NON
signer certificat = NON
Pas de restore d'interface

ENSUITE UTILISER UNE VM WINDOWS 
ajouter une carte réseau, le même réseau c'est à dire VMNET10 si tu as mis 10 dans l'autre VM

Pour l'instant il ne sert que de routeur (box de la maison)

Mettre l'adresse ip dans la barre de recherche et on arrive sur le navigateur de opnsense
Username : root
mdp : opnsense

Dans Wizard
cliquer sur suivant et modifier le langage
On va mettre le DNS de google (8.8.8.8)
Activer le résolveur
Timezone en EU/Paris

Pare-feu près à l'usage
On va s'en servir comme plateforme pour le proxy

Ensuite

Aller dans l'onglet système puis firmware et mise à jour
Puis dans statut et vérifier les mises à jour

Créer une certificat SSL
Se rendre dans système, gestion des certificats puis autorités et cliquer sur le '+'
Créer une autorité de certificat internet
Description : certificat_SSL
Pays France
Grand est
Metz
Organisation : MNS
Puis il faut le télécharger (en certificat)
Renommer son extension en .crt
En gros c'est à dire qu'on le met en confiance 
Par exemple pour une entreprise, faire une GPO ou un script
Double clique sur le certificat, il propose de l'installer = on l'installer sur l'ordinateur local
On le place dans le magasin 'autorité  de certification racine de confiance'
C'est bon le certificat est bien importé

On s'occupe du proxy maintenant

On se rend dans "système", 'firmware', et "greffons"
On cherche dans la barre de recherche le proxy "squid" et on l'installe
On redémarre OPNSENSE, dans le menu alimentation

On relance 

On va dans squid Web Proxy puis dans forward proxy et on va signifier sur quel interface le proxy va être intégrer, on laisse le port de proxy par default
Certificat à utiliser = celui qu'on a utiliser précédemment
Se rendre dans les paramètres généraux
Activer le proxy, puis cliquer la petite flèche et aller dans les paramètres du cache local
Cocher la case = stocker sur le proxy et non sur les caches des utilisateurs, il n'y aura pas de cache sur les navigateurs

Cookie : fichier qui se stock sur l'ordinateur (traçage), se qui te garde connecter, ou qu'il garde ton panier d'achat

Puis on applique
Maintenant le proxy et en route

On va créer de règles de filtrage dans le pare-feu
On va faire une déviation, on va faire que ça passe dans le proxy

On va se rendre dans le pare-feu, dans les règles. On va faire une règle dans le LAN
En gros on bloque tout le trafic HTTP
Créer 2 nouvelles règles : ajouter,
créer l'action bloquer le protocole TCP
Dans source : LAN net
Description : bloquage HTTP pour forcer le PROXY
Puis on sauvegarde
Et on duplique et modifie juste le HTTP en HTTPS dans la duplication
Les règles les plus hautes sont prioritaires, il faut les monter d'un niveau
Cocher les deux et cliquer la flèche du premier
Puis appliquer "les changements"

On a plus accès à internet car bloquer les trafic HTTP et HTTPS
Mais on peut re accéder à internet manuellement
En tapant proxy dans la barre de recherche
On va renseigner l'adresse IP du proxy : 192.168.1.254 sur le port 3129


Se rendre dans Squid Web -> Administration et activer le proxy transparent et l'inspection SSL
Penser a désactiver le proxy manuel
Faire pareil sur proxy HTTP transparent -> sur le lien orange et appliquer les changements
Tout est prérempli on doit juste sauvegarder
Petit I : ajouter la règle et on la sauvegarde et on "applique les changements"
Normalement on retrouve la connexion internet

Dans proxy -> Administration -> Liste de contrôle d'accès
Ajouter une liste "Black list", on doit taper une url
Description : black list
Puis on télécharge les ACLs "télécharger ACL"
Editer la liste noir, sélectionner social network
appliquer
Et télécharger ACLs
.





