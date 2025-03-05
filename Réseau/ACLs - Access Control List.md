

2 Types différents :
- Standard : 
	- Numérotée : 1 à 99 et 1300 à 1999
	- Faire un filtrage : IPv4 source et Destination / IPv6 source et Destination
		- Ports, protocoles, @MAC(option)


- Etendue :
	- Numérotée : 100 à 199 et 2000 à 2699
	- Elles peuvent aussi être nommées : exemple : deny ICMP

Résumé :
- Il existe **deux types principaux d’ACLs** :

	- **ACLs Standards** : filtrent uniquement selon l’adresse IP source.
	- **ACLs Étendues** : filtrent selon l’adresse IP source et destination, les protocoles et les ports.


Les ACLs standards se positionnent toujours plutôt proche de la destination.
On peut mettre des interdictions (ACLs) en entrée et en sortie (exemple : Deny IPv4).
ACl étendue sur une interface, étendue permet de bloquer plutôt près de la source à contrario des standards.

Une ACL en entrée et en sortie par interface.
On peut mettre une en IN et une en OUT par interface
On peut aller jusqu'à 4 ACL par interface (ce sont des panneaux pour mettre les règles de cheminement), par exemple quelqu'un d'extérieur qui voudrait venir de l'extérieur.

Les ACL réseau gèrent l’accès à un réseau. Pour ce faire, ils fournissent des instructions aux commutateurs et routeurs quant aux types de trafic qui sont autorisés à s’interfacer avec le réseau. Ils dictent également ce que chaque utilisateur ou appareil peut faire une fois qu’il est à l’intérieur.

Lorsque les ACL ont été conçus pour la première fois, ils fonctionnaient comme des [pare-feux](https://www.fortinet.com/fr/resources/cyberglossary/how-does-a-firewall-work), bloquant l’accès aux entités indésirables. Alors que de nombreux pare-feux disposent de fonctions de contrôle d’accès au réseau, certaines organisations utilisent toujours des ACL avec des technologies telles que les réseaux privés [virtuels (VPN](https://www.fortinet.com/fr/resources/cyberglossary/what-is-a-vpn)). De cette manière, un administrateur peut dicter les types de trafic qui sont chiffrés, puis envoyés via le tunnel sécurisé du VPN.

Les ACL, pour Access Control List, sont des règles appliquées aux trafics transitant via les interfaces du routeur que ce soit en entrée (in) ou en sortie (out). Les ACL filtrent le trafic en demandant aux interfaces d’acheminer ou non les paquets qui y transitent. Pour ce faire, le routeur lit l'en-tête de chaque paquet afin de déterminer s'il doit être acheminé ou non en fonction des conditions définies dans la liste de contrôle d’accès ACLs.


- Mots clés : 
	- Any
	- Host
	- Established (ACL étendue)

- Wild card (inverse du subnet mask)
	-  255 255 255 255 - 255 255 255 0 / 24
	= 0.0.0.255
- 255.255.255.255 - 255.255.255.192 / 26
	= 0.0.0.64


Trouver le nom d'un réseau : mettre tout en binaire

ACL sont composées d'ACE (Access Control Elements)

access-list

ip access-list

Vérification :
- show access-list
- show ip interface

![[Pasted image 20250305091946.png]]


Jeux : binary game

 