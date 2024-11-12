
05/11/24

#### Modifier le nom d’un host :
en
conf t
host (le nom)
exit


#### Création d'une interface virtuelle :

int vlan 10

![[Pasted image 20241105114337.png]] 


#### Voir les IP des interfaces :

sh ip in brief



#### Commande pour ne plus que ça soit un port de switch (c'est maintenant un port de routeur)

 ![[Pasted image 20241105115458.png]]




Prévoir les routes de retour (si tu veux rejoindre le subnet mask) :

ip route .....

![[Pasted image 20241105120150.png]] 


Il faut que les vlan soit sur tous les switch 

![[Pasted image 20241105121601.png]] 


Donne une adresse IP et son mask a un routeur 

![[Pasted image 20241105135909.png]]  


![[Pasted image 20241105140155.png]]


Création de vlan qui peuvent communiquer mais les pc ne peuvent pas se ping entre eux car ils ne sont pas dans le même réseau 

![[Pasted image 20241105141002.png]]


![[Pasted image 20241105141211.png]]

rajouter un câble en plus de F0/14 à F0/14 pour que les pc communique

![[Pasted image 20241105141340.png]]


Une autre facon pour qu'il communique en lien trunk avec les ports

![[Pasted image 20241105141942.png]] 

