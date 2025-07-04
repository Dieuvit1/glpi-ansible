#  Déploiement automatique de GLPI avec Ansible

Ce projet permet d’automatiser l’installation et la configuration de GLPI sur un serveur Ubuntu grâce à Ansible.  
Il installe les composants suivants :

- Apache2
- PHP avec les modules nécessaires
- MariaDB (serveur de base de données)
- GLPI (outil de gestion de parc informatique)
- Configuration de la sécurité (UFW + SSL auto-signé)

## Prérequis

### Système cible
- Ubuntu 20.04 ou 22.04
-  Accès SSH avec privilèges sudo

### Machine de contrôle (où Ansible est installé)
- Ansible (version 2.10+ recommandé)
- Python 3

### Installer Ansible sur votre machine de contrôle :
```bash
sudo apt update
sudo apt install ansible -y

Manuel d’installation

1.  Cloner le dépôt
bash
Copier
Modifier
git clone https://github.com/Dieuvit1/glpi-ansible.git
cd glpi-ansible

2.  Modifier l’inventaire
Dans le fichier inventory/hosts, indiquez l’adresse de votre serveur GLPI :

ini
Copier
Modifier
[glpi]
glpi.local ansible_user=glpi ansible_become=true
Remplacez glpi.local par l’adresse IP ou le nom DNS de votre serveur.

3. Lancer l'installation
L'installation complète se fait via ce playbook :

bash
Copier
Modifier
ansible-playbook -i inventory/hosts playbooks/install-glpi.yml

Ensuite, configurez la base de données :

bash
Copier
Modifier
ansible-playbook -i inventory/hosts playbooks/setup-database.yml
Et enfin, sécurisez le serveur :

bash
Copier
Modifier
ansible-playbook -i inventory/hosts playbooks/secure-server.yml


Structure du projet
bash
Copier
Modifier
glpi-ansible/
├── inventory/
│   └── hosts
├── playbooks/
│   ├── install-glpi.yml
│   ├── setup-database.yml
│   └── secure-server.yml
├── roles/
│   ├── apache/
│   │   └── tasks/main.yml
│   ├── php/
│   │   └── tasks/main.yml
│   ├── mariadb/
│   │   └── tasks/main.yml
│   └── glpi/
│       └── tasks/main.yml
└── README.md

 Accès à GLPI
Après l’installation, accédez à GLPI via un navigateur :

Copier
Modifier
http://<IP_DU_SERVEUR>/glpi
ou en HTTPS si SSL est activé :

Copier
Modifier
https://<IP_DU_SERVEUR>/glpi

Auteur
Dieuvit BOUNGUILI-KOUA
Thanina YATAGHANE

GitHub : github.com/Dieuvit1

Projet : Automatisation déploiement GLPI avec Ansible
