


1. ## Configuration réseau de server1
    
    1. **Lister les interfaces réseau disponibles** : ip addr show
        
    
    Vous devriez voir au moins deux interfaces, par exemple `enp0s3` (NAT) et `enp0s8` (intnet).  
    
    2. **Configurer l'interface NAT (Interface 1)** :
        
        - Éditez le fichier `/etc/network/interfaces` : sudo nano /etc/network/interfaces
        
        Ajoutez ou modifiez les lignes pour l'interface NAT : auto enp0s3 iface enp0s3 inet dhcp
        
    
    Assurez-vous que l'interface NAT est configurée pour démarrer automatiquement (`auto`), sinon elle sera inactive après un redémarrage du service réseau.
    
    3. **Configurer l'interface interne (Interface 2)** : Ajoutez les lignes suivantes pour l'interface interne : auto ens33 iface ens33 inet static address 192.168.200.254 netmask 255.255.255.0
    
    4. **Redémarrer le service réseau** : sudo systemctl restart networking
    5. **Vérifier la configuration des interfaces** : ip addr show ens33 ip addr show ens37
    
    6. **Vérifier l'accès à Internet** : ping -c 4 google.com
    
    ## Configuration réseau de server2
    
    1. **Lister les interfaces réseau disponibles** : ip addr show (ens33)
    2. **Configurer l'interface interne avec une IP statique** :
        
        - Éditez le fichier `/etc/network/interfaces` : sudo nano /etc/network/interfaces
        
    
    4. **Redémarrer le service réseau** : sudo systemctl restart networking
    5. **Vérifier la configuration** : ip addr show ens33
    6. **Tester la connectivité avec Server1** : ping -c 4 192.168.200.254
    
    (modifié)

    
    ## Configuration réseau du client Windows
    
    1. **Configurer l'interface réseau** :
        
        - Accédez aux paramètres de votre carte réseau.
        - Modifiez les propriétés de **Protocole Internet version 4 (TCP/IPv4)**.
        - Entrez les informations suivantes :
            
            - **Adresse IP** : `192.168.200.1`
                
                - **Masque de sous-réseau** : `255.255.255.0`
                - **Passerelle par défaut** : `192.168.200.254`
                - **Serveur DNS préféré** : `192.168.200.254`
                
            
        
    2. **Tester la connectivité avec les serveurs** :
        
        - Ouvrez l'invite de commandes : ping 192.168.200.254 ping 192.168.200.2


