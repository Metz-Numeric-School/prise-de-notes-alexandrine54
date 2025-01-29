
Filezila = Est un programme ou « client » FTP (File Transfer Protocol) qui permet aux utilisateurs de déplacer des fichiers entre des ordinateurs en utilisant Internet**. Cela signifie que les gens utilisent FileZilla pour accomplir plusieurs tâches, telles que : Téléverser des fichiers. Télécharger des fichiers.
### Créer une machine virtuelle 

écrire ces commande dans putty pour qu'on puisse installer l'iso de OpnSense dans le pnetlab

cd /opt/unetlab/addons/qemu/opnsense-24.7/  
  
/opt/qemu/bin/qemu-img create -f qcow2 virtioa.qcow2 10G  
  
cd  
  
/opt/unetlab/wrappers/unl_wrapper -a fixpermissions


Grace à ça on peut créer des vm dans des vm


+$