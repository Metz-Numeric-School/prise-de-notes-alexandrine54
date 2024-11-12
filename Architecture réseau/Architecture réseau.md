

172.16.0.0 /23

Sales 200 : il nous faut un bloc de 256; 172.16.0.0 > 172.16.0.255 /24
R&D 50 : bloc de 64; 172.16.1.0 > 172.16.1.63 /26
MGT 25 : bloc de 32 adresses; 172.16.1.64 > 172.16.1.95 /27
IT 10 : bloc de 16 adresses; 172.16.1.96 > 172.16.1.111 /28
PRINTERS 10 : bloc de 16 adresses; 172.16.1.112 > 172.16.1.127 /28
SERVERS 10 bloc de 16 adresses; 172.16.1.128 > 172.16.1.144/28

10 puissance 4 = 10 000 : décimal plage d'adresse
2 puissance 4 = 16 : binaire plage d'adresse

10 10 11 01 = décomposition en puissance de 2 : 2 puissance 0, 2 puissance 1 ... etc

![[Pasted image 20241104091419.png]]

soustraction, à chaque fois soustraire celui d'avant avec celui d'après
 
7 couches d'OSI

![[Pasted image 20241104092539.png]]


composant pour le 1 : câble Ethernet, câble coaxial, câble série, Fibre, Ondes électromagnétique (wifi Bluetooth, sans fil),  hub (concentrateur), message = bit 
composant pour le 2 : switch, adresse MAC (48bits), message =  Trames/Fram
composant pour le 3 : routeur, @ipv4 (32bits), @ipv6 (128bits), message = Paquets/Packet
	compostant pour le 4 : Firewall (pare-feu), Port (16bits), message = Segment
composant pour le 5 : message = donnée
composant pour le 6 : message = donnée
composant pour le 7 : message = donnée


il y a 5 classes

![[Pasted image 20241104095928.png]] 

classe D = on l'utilise pas
classe E = réservée


254 255 255 254
254 255 255 255
255   0     0     0


![[Pasted image 20241104112512.png]]  


![[Pasted image 20241104115103.png]] 




Mode commande :

enable
conf t
vtp mode client
vtp domain BSRC2
vtp password


enable
conf t
vtp mode server
vtp domain BSRC2
vtp password
