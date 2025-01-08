

interface gigabitEthernet 0/0
switchport mode trunk
switchport trunk encapsulation dot1q


Dans ce cas précis, le but du trunk est de permettre au trafic de plusieurs VLANs de passer entre le switch et le routeur (ou entre deux switches).
Pourquoi utiliser un trunk ?
Les VLANs segmentent le réseau en plusieurs sous-réseaux logiques.
Un port en mode access ne peut transporter le trafic que d'un seul VLAN.
Le mode trunk permet à un port de transporter le trafic de plusieurs VLANs en utilisant un marquage (tagging) appelé 802.1Q.