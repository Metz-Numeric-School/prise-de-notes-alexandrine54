
Switch : Full Duplex
envoie et répond en simultanément, parler en écouter en même temps = moins de collision et ça va plus vite. 

Hub : Half duplex


**Le terme duplex** est utilisé pour décrire un canal de communication qui peut transporter des signaux dans les deux sens, contrairement à un canal simplex, qui porte un signal que dans une seule direction.


# Half-Duplex

Quand on branche une carte réseau sur un HUB, on utilise la même paire de cuivre **pour l’aller et pour le retour**. Donc il faut forcément qu’une entité se taise pour que l’autre puisse lui envoyer une donnée. Comment savoir si en face on parle ? Grâce à la méthode CSMA/CD (lire le chapitre [CSMA/CD](https://reussirsonccna.fr/la-methode-csmacd-tout-ca-pour-ca/) pour comprendre). Ce fonctionnement se nomme **Half-Duplex**.

Aujourd’hui, on n’utilise plus les HUB dans un réseau (enfin j’espère pour vous) car au final les débits sont très faibles (10Mb/s voir 100Mb/s). A la place, on met des switchs pour raccorder les machines entre elles et nous permettre de faire du Full-Duplex.

# Full-Duplex

Un des avantages du switch est qu’il peut utiliser une paire de cuivre pour l’aller **et une autre** paire de cuivre pour le retour donc au lieu d’être en fonctionnement « Talkie-Walkie » comme le Hub, chacun peut parler simultanément car on utilise des chemins physiques différents donc impossible d’avoir une collision. Ce fonctionnement se nomme **Full-Duplex**.



![Configure Switch Ports (2.1.2) > Cisco Networking Academy's Introduction to  Basic Switching Concepts and Configuration | Cisco Press](https://www.ciscopress.com/content/images/chap2_9781587133183/elementLinks/02fig07_alt.jpg)