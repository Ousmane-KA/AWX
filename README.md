# AWX


-------- 

![image](https://github.com/user-attachments/assets/6354ceff-b337-48ee-8d64-32ed72e6e441)


--------



## Documentation d'Installation d'AWX

### 1. Installation de Docker et Docker Compose

#### Installation Docker

On exécute les commandes suivantes pour installer Docker :

```bash
curl -fsSL https://get.docker.com -o get-docker.sh 2>&1
chmod 775 get-docker.sh
./get-docker.sh
```


Ensuite, On démarre le service Docker et ajoutez votre utilisateur au groupe Docker :

```bash
service docker start
usermod -aG docker root
docker --version
```



#### Installation de Docker Compose

On exécute les commandes suivantes pour installer Docker Compose :

```bash
sudo curl -L "https://github.com/docker/compose/releases/latest/download/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
sudo chmod +x /usr/local/bin/docker-compose
docker-compose --version
```

### 2. Installation d'Ansible

On exécute la commande suivante pour installer Ansible :

```bash
apt install -y ansible
```

### 3. Installation de Python 3 et des modules pour Docker

#### Installation de Python 3

On exécute la commande suivante pour installer Python 3 et pip :

```bash
sudo apt-get install -y python3 python3-pip
python3 --version
```



#### Installation des modules Docker et Docker Compose

On exécute la commande suivante pour installer les modules Python nécessaires :

```bash
pip3 install docker docker-compose --user
```



### 4. Installation d'AWX

#### Clonage du dépôt AWX

On clone le dépôt officiel AWX avec la version souhaitée (ici, la version 17.1.0) :

```bash
sudo git clone -b 17.1.0 https://github.com/ansible/awx.git
```



#### Modification du fichier `inventory`

On édite le fichier `inventory` pour adapter la configuration à votre environnement.



#### Déploiement de AWX avec Ansible

On exécute la commande suivante pour déployer AWX via Ansible :

```bash
ansible-playbook -i inventory install.yml
```



#### Vérification des conteneurs Docker

Pour vérifier si les conteneurs AWX sont en cours d'exécution, on utilise la commande suivante :

```bash
docker ps
```



#### Création d'un utilisateur administrateur

Pour créer un utilisateur administrateur:

> On se connectez-vous au conteneur

```bash
docker exec -it awx /bin/bash

```


On exécute la commande suivante :

```bash
awx-manage createsuperuser
```


#### Accéder à l'interface Web d'AWX

Après l'installation et la configuration, On peut accéder à l'interface web d'AWX via votre navigateur. 

![image](https://github.com/user-attachments/assets/e4390160-cea5-4024-9678-9a84693d2f38)

