


DNS = Domain Name System
Système de gestion de noms de domaines

L'ICANN est un organisme qui gère la liste des Top Level Domain (TLD)

Il existe une TLD par pays
(.fr pour France, .it pour Italie, .de pour Allemagne etc.) et quelques TLD générales (.com, .tv, .org, .mil, .biz...)

L'ICANN délègue la gestion de chaque TLD à un organisme (registry).

Les registry doivent tenir à jour la liste des domaines définis sur sa ou ses TLD.
AFNIC tient le registre des .fr
VeriSign tient le registre des .com/.net/.org/.info/.biz.

Chaque registry peut gérer comme bon lui semble l'attribution des noms de domaine sur sa TLD

Les registry ont un rôle technique

Chaque registry autorise des registrars à vendre des noms de domaine

Les registrars ont un rôle commercial.


Chaque pays possède un TLD qui correspond à son code pays ISO

On les appelle ccTLD (Country-code TLD)

La gestion de ces TLD repose sur des serveurs racine (appelés DNS root server)

Le service = Permet la correspondance entre un nom de domaine qualifié FQDN (Fully Qualified Domain Name) et une adresse IP.

#### Domaine Inverse

Résolution d'une adresse IP en nom de domaine spécial in-addr.arpa à la fin.

exemple : réseau 10.1.0.0.Adresse Inverse : 1.10.in-addr.arpa

#### Délégation 

Transfer de responsabilité 



#### Zone primaire et zone secondaire

Transfert de zones entre serveur maître (primaire) et un autre serveur (secondaire), chacun ayant autorité sur la zone. Vis-à-vis d'un client, l'un ou l'autre répond en fonction de la vitesse du réseau.


#### Scénarios possibles

- Serveur cache
- Serveur primaire (maître)
- Serveur secondaire (esclave)
- Serveur stub

#### Serveur cache

But : Effectuer des requêtes DNS pour se rappeler de la réponse pour la prochaine requête.

Avantages : Réduction de la bande passante, réduction du temps de latence

La box peut faire cache DNS.

#### Serveur primaire (maître)

But : Contenir des enregistrements DNS d'un nom de domaine enregistré

Un ensemble d'enregistrements DNS pour un nom de domaine est appelé une "zone"

Le nom de domaine peut être imaginaire, mais seulement sur un réseau local fermé, non connecté à Internet.

#### Serveur secondaire (esclave)

But : Contenir une copie des zones configurées sur le serveur maître.

Avantages : Recommandé sur les réseaux importants, assure la disponibilité de la zone DNS si le serveur maître n'est pas disponible.


#### Serveur stub

But : Idem que le serveur esclave, mais copie uniquement les données du serveur et pas les données de l'hôte.

#### Enregistrements DNS

But : mapper nom d'hôte / adresse IP et adresse IP/ nom d'hôte

![[Pasted image 20241015093222.png]]


#### Les redirecteurs

### Pourquoi configurer les redirecteurs sur les deux serveurs DNS (primaire et secondaire) ?

- **Redondance** : Si votre serveur DNS primaire rencontre un problème ou est hors ligne, les clients peuvent toujours utiliser le serveur DNS secondaire pour résoudre les noms de domaine internes et externes.
- **Performance** : Le fait de configurer les redirecteurs sur les deux serveurs permet aux deux d’être capables de gérer les requêtes externes. Ainsi, vous répartissez la charge entre les deux serveurs.
- **Continuité** : Dans une configuration DNS maître/esclave, le serveur secondaire ne sert pas seulement de secours, mais peut aussi répondre aux requêtes des clients. Si le serveur secondaire ne dispose pas de redirecteurs configurés, il ne pourra pas résoudre les noms de domaine externes si le serveur primaire est indisponible.


### Pourquoi utiliser les DNS publics de Google (8.8.8.8 et 8.8.4.4) ?

1. **Fiabilité** : Les serveurs DNS de Google sont extrêmement stables et disponibles dans le monde entier. Ils sont conçus pour offrir une réponse rapide et fiable aux requêtes DNS, avec des infrastructures réparties géographiquement pour garantir la disponibilité.
    
2. **Performance** : Les serveurs DNS publics de Google sont souvent très rapides car ils sont optimisés pour offrir des temps de réponse courts. L'utilisation de ces serveurs peut réduire le temps nécessaire à la résolution des noms de domaine, améliorant ainsi la navigation Internet pour les utilisateurs.
    
3. **Simplicité d'utilisation** : Google DNS offre une alternative simple et gratuite aux serveurs DNS de votre fournisseur d'accès à Internet (FAI). De plus, les adresses IP **8.8.8.8** et **8.8.4.4** sont faciles à retenir, ce qui les rend pratiques pour des configurations rapides.
    
4. **Globalité** : Contrairement aux serveurs DNS d'un FAI qui sont généralement limités à une région spécifique, les serveurs DNS de Google sont accessibles et performants dans presque tous les pays. Cela les rend utiles pour des réseaux distribués ou pour des entreprises avec des bureaux dans plusieurs régions.
    
5. **Sécurité et mise à jour** : Google assure que ses serveurs DNS sont régulièrement mis à jour et protégés contre diverses attaques DNS comme les attaques DDoS ou le cache poisoning. Ils incluent également des fonctionnalités de sécurité supplémentaires comme **DNSSEC** pour vérifier l'intégrité des requêtes DNS.