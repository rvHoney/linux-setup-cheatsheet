# Installation de WORDPRESS sur un serveur LAMP.
Maintenant que notre serveur **LAMP** est installé il est possible d'installer **Wordpress**.

## Installation de Wordpress
Connectez-vous sur votre serveur Linux en SSH afin de télécharger l'archive ZIP qui contient les sources de WordPress.

### Téléchargement de l'archive.
> 1) cd /tmp
> 2) wget https://wordpress.org/latest.zip -e use_proxy=yes -e **https_proxy=adresseduproxy**:**port**

### Créer une base de données pour Wordpress
> 1) mariadb
> 2) CREATE DATABASE **nom_de_la_base**;
> 3) SHOW DATABASES;
> 4) CREATE USER '**nom_d_utilisateur**'@'localhost' IDENTIFIED BY '**mot_de_passe**';
> 5) GRANT ALL PRIVILEGES ON **nom_de_la_base**.* TO **nom_d_utilisateur**@localhost;
> 6) FLUSH PRIVILEGES;
> 7) exit

### Décompresser l'archive Wordpress à la racine du site
> 1) rm /var/www/html/index.html

### Installer le paquet zip pour le décompresser et le décompresser
> 1) sudo apt-get update 
> 2) apt-get install zip
> 3) unzip latest.zip -d /var/www/html

### Déplacer le contenu du dossier wordpress à la racine du site.
> 1) cd /var/www/html
> 2) mv wordpress/* /var/www/html/
> 3) rm wordpress/ -Rf

### Donner les droits à l'utilisateur "www-data" (apache2).
> 1) chown -R www-data:www-data /var/www/html/

**Voilà !** Wordpress est installé ! Pour le configurer il ne vous reste plus qu'à entrer votre adresse IP dans votre navigateur.
