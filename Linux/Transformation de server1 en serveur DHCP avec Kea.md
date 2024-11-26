

**Détails des messages :**

- **DHCPDISCOVER** : Le client recherche les serveurs DHCP sur le réseau.
- **DHCPOFFER** : Le serveur propose une adresse IP et des paramètres de configuration.
- **DHCPREQUEST** : Le client accepte l'offre du serveur et demande la configuration.
- **DHCPACK** : Le serveur confirme la configuration et l'allocation de l'adresse IP.

### **Rôles du serveur et du client DHCP**

- **Serveur DHCP :**
    
    - Gère un pool d'adresses IP disponibles pour les clients.
    - Alloue des adresses IP aux clients selon des politiques définies.
    - Fournit des informations de configuration supplémentaires (passerelle, DNS, etc.).
    - Gère la durée des baux (leases) et le renouvellement des adresses IP.
- **Client DHCP :**
    
    - Demande une configuration réseau au serveur DHCP.
    - Renouvelle son bail périodiquement avant expiration.
    - Libère l'adresse IP lorsqu'il n'en a plus besoin (par exemple, à l'extinction).