# Projet A:
# Automatisation de reboot sanitaire des serveurs


C'est quoi un **reboot** planifié? 
C'est une **opération de maintenance**, aussi récurrente que nécessaire dont le but d’améliorer la fiabilité, les performances et la sécurité de l’infrastructure.

 - **Parties du projet**
    -  Système
    -  Socle Infrastructure
    -  Automatisation
    -  Développement Python / Ansible

    
   Système (Environnement):  Ubuntu 22.04, ansible [core 2.13.4], python3
   Socle Infrastructure:
    *sous VMWare ,  j'ai créé 3 machines virtuelles: 
    - VM master: Contrôle Node où ansible est installé obligatoire
    - VM slave: Managed Node 1 python3 par nécicité
    - VM slave: Managed Node 2 python3 par nécicité


    Automatisation: script pour automatiser le reboot d'un serveur via ansible  


![Bonjour](\home\malikablg\Documents\projetansible\images\diagramme_infra.png)

   Pour mon playbook "reboot_sanitaire.yaml":
    
 - Check l'état initial des services installés
 - Stopped and Disabled les services en state "running"
 - Lance le reboot des serveurs avec un timing de 5min(600 s)
 - Restart and Enabled les services en state "stopped"
 - Check l'état final des services installés
  
  Afin de fonctionner mon playbook  "reboot_sanitaire.yaml" , j'ai opter à installer des services sur mes deux VMs.  Pour cela, j'ai créer un autre playbook "services_install.yaml":
  
  Slave1 : 
   - installe le serveur LAMP ( apache, php, mysql
   
 Slave2:
 - installe haproxy
 - installe ftp
   

