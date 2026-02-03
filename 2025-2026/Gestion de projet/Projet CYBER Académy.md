

### Contexte : 
La **Metz Cyber Academy (MCA)** est un établissement d’enseignement supérieur privé spécialisé en **cybersécurité**, existant depuis plus de 9 ans, accueillant **plus de 500 apprenants par an** et comptant **25 collaborateurs permanents** sur le site principal de Metz. Elle dispose actuellement de **deux sites** (Technopôle et Centre Gare), dont un nouveau site dédié au programme **« Spécialiste Cyberdéfense »** qui doit accueillir **20 apprenants supplémentaires** avec des besoins techniques avancés Le **système d’information actuel** a été déployé progressivement et repose sur des technologies **obsolètes**, en grande partie **hors support**, avec une architecture peu résiliente. Un **incident majeur récent** a provoqué une **coupure totale d’Internet pendant 5 jours**, impactant fortement l’activité pédagogique et administrative, ce qui a mis en évidence la **nécessité urgente de moderniser le SI** La direction souhaite un SI aligné avec les valeurs de l’école : **performance, résilience, sécurité et conformité**, tout en accompagnant la croissance future et l’ouverture du nouveau cursus. 

### Contraintes :
#### Contraintes organisationnelles - 
Équipe IT réduite (2 techniciens dédiés à l’infrastructure). - Fonctionnement actuel essentiellement **réactif**, peu de temps pour l’anticipation. - Continuité de service indispensable pour les apprenants et l’administration. 
#### Contraintes techniques 
Infrastructures **vieillissantes** (ESXi 5.5, Windows Server 2012 R2, Exchange 2016). - Absence de redondance (Internet, hyperviseur, pare-feu). - Segmentation réseau très basique (2 VLAN). - Aucun lien inter-site. - Pas d’infrastructure pédagogique dédiée pour le cursus Cyberdéfense. - Sauvegardes non conformes aux standards actuels (pas de tests, pas de 3-2-1-1-0). 
#### Contraintes budgétaires - **CAPEX** : 
- 100 000 € HT pour la modernisation globale
- 50 000 € HT dédiés au projet « Spécialiste Cyberdéfense » 
- **OPEX** : - 30 000 € HT par an sur 5 ans (cloud, cybersécurité, support) 
- Tolérance de dépassement possible de ±20 % si justifiée. 
- Éligibilité aux **licences Éducation** des éditeurs 
#### Contraintes réglementaires et normatives 
- Conformité **RGPD**. 
- Respect des **recommandations ANSSI**. 
- Exigences strictes liées à une **assurance cyber** (MFA, SIEM, EDR, Zero Trust, PRA/PCA). 
### Enjeux : 
#### Enjeux business 
- Éviter les pertes financières liées aux interruptions (≈ **20 000 € HT / jour** d’arrêt).
- Préserver l’image et la crédibilité d’une école spécialisée en cybersécurité. 
- Garantir la continuité pédagogique et administrative. 
- Accompagner la croissance (+20 % d’apprenants estimée sur 5 ans). 
- Offrir des services numériques fiables et modernes aux apprenants. 
#### Enjeux techniques 
- Moderniser l’infrastructure (virtualisation, réseau, sauvegarde). 
- Mettre en place une **haute disponibilité** et de la **redondance**. 
- Intégrer une infrastructure dédiée et isolée pour le cursus Cyberdéfense. 
- Automatiser les déploiements et la gestion des utilisateurs.
- Mettre en place une supervision centralisée et proactive. 
- Atteindre les objectifs **RTO/RPO** définis : 
- RTO SI interne : 8 h
- RTO Internet : 1 h
- RPO : 8 h 
#### Enjeux de sécurité 
- Élever drastiquement le niveau de cybersécurité (actuellement très faible).
- Protéger les données administratives et pédagogiques.
- Sécuriser les accès (MFA, authentification forte, Zero Trust).
- Mettre en place EDR, SIEM, journalisation centralisée. 
- Chiffrement des flux et des données. 
- Sécurisation du réseau pédagogique (BYOD). 
- Mise en conformité pour l’assurance cyber.