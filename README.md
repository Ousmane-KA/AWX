# AWX

## Documentation d'Installation d'AWX

### 1. Installation de Docker et Docker Compose

#### Installer Docker

Exécutez les commandes suivantes pour installer Docker :

```bash
curl -fsSL https://get.docker.com -o get-docker.sh 2>&1
chmod 775 get-docker.sh
./get-docker.sh
```

![Docker installation](https://prod-files-secure.s3.us-west-2.amazonaws.com/aa33cd60-ad5b-4319-acee-315d210bdb02/c27fd2b2-16dd-4e8c-9746-23fb36410c6f/image.png)

Ensuite, démarrez le service Docker et ajoutez votre utilisateur au groupe Docker :

```bash
service docker start
usermod -aG docker root
docker --version
```

![Docker version](https://prod-files-secure.s3.us-west-2.amazonaws.com/aa33cd60-ad5b-4319-acee-315d210bdb02/4958e846-50dc-4f41-9811-c710a180e536/image.png)

#### Installer Docker Compose

Exécutez les commandes suivantes pour installer Docker Compose :

```bash
sudo curl -L "https://github.com/docker/compose/releases/latest/download/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
sudo chmod +x /usr/local/bin/docker-compose
docker-compose --version
```

![Docker Compose installation](https://prod-files-secure.s3.us-west-2.amazonaws.com/aa33cd60-ad5b-4319-acee-315d210bdb02/6867382d-25a0-41a2-8b06-7135716940ff/image.png)

### 2. Installation d'Ansible

Exécutez la commande suivante pour installer Ansible :

```bash
apt install -y ansible
```

### 3. Installation de Python 3 et des modules pour Docker

#### Installer Python 3

Exécutez la commande suivante pour installer Python 3 et pip :

```bash
sudo apt-get install -y python3 python3-pip
python3 --version
```

![Python3 installation](https://prod-files-secure.s3.us-west-2.amazonaws.com/aa33cd60-ad5b-4319-acee-315d210bdb02/714bfddd-2be3-463a-9848-295c39aa2894/image.png)

#### Installer les modules Docker et Docker Compose

Exécutez la commande suivante pour installer les modules Python nécessaires :

```bash
pip3 install docker docker-compose --user
```

![Python modules installation](https://prod-files-secure.s3.us-west-2.amazonaws.com/aa33cd60-ad5b-4319-acee-315d210bdb02/f6967a39-24f9-4958-aa76-32ff9c306440/image.png)

### 4. Installation d'AWX

#### Cloner le dépôt AWX

Clonez le dépôt officiel AWX avec la version souhaitée (ici, la version 17.1.0) :

```bash
sudo git clone -b 17.1.0 https://github.com/ansible/awx.git
```

![Clone AWX](https://prod-files-secure.s3.us-west-2.amazonaws.com/aa33cd60-ad5b-4319-acee-315d210bdb02/1ee87548-e42e-45de-9e0c-cf6e78ce0850/image.png)

#### Modifier le fichier `inventory`

Éditez le fichier `inventory` pour adapter la configuration à votre environnement.

![Edit inventory](https://prod-files-secure.s3.us-west-2.amazonaws.com/aa33cd60-ad5b-4319-acee-315d210bdb02/7e1638d8-9ebe-453a-b016-3cdb6ba95f2b/image.png)

#### Déployer AWX avec Ansible

Exécutez la commande suivante pour déployer AWX via Ansible :

```bash
ansible-playbook -i inventory install.yml
```

![Deploy AWX](https://prod-files-secure.s3.us-west-2.amazonaws.com/aa33cd60-ad5b-4319-acee-315d210bdb02/431791ff-ac74-4ae0-b8ef-56dadb8b3d86/image.png)

#### Vérifier les conteneurs Docker

Pour vérifier si les conteneurs AWX sont en cours d'exécution, utilisez la commande suivante :

```bash
docker ps
```

![Docker ps](https://prod-files-secure.s3.us-west-2.amazonaws.com/aa33cd60-ad5b-4319-acee-315d210bdb02/f55015ab-cef4-49f8-a68d-f6b12f576ec6/image.png)

#### Créer un utilisateur administrateur

Pour créer un utilisateur administrateur, connectez-vous au conteneur et exécutez la commande suivante :

```bash
awx-manage createsuperuser
```

![Create superuser](https://prod-files-secure.s3.us-west-2.amazonaws.com/aa33cd60-ad5b-4319-acee-315d210bdb02/67c69635-f98c-46b6-a8a6-4b37d2c3ec3a/image.png)

#### Accéder à l'interface Web d'AWX

Après l'installation et la configuration, vous pouvez accéder à l'interface web d'AWX via votre navigateur. L'URL de l'interface web sera définie par la configuration de votre instance Docker et d'AWX.
