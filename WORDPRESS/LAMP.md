# Installation d'un serveur LAMP pour utiliser WORDPRESS.
Afin d'utiliser **Wordpress** il est nécessaire de configurer une serveur **LAMP** (*Linux* *Apache* *MariaDB* *PHP*).  
Une fois cette étape terminée il sera possible de commencer à installer **Wordpress**.

### Se connecter en root et mettre à jour les paquets.
> 1) su -
> 2) apt-get update   

## Installation d'Apache.
Maintenant que les paquets sont à jour nous pouvons passer à l'installation de Apache. Apache est un serveur HTTP permettant d'héberger notre site.  

### Installation du paquet apache2.
> 1) apt-get install -y apache2

### Activer le démarrage automatique d'Apache au lancement.
> 1) systemctl enable apache2

### Activation de plusieurs modules d'Apache.
> 1) a2enmod rewrite *(réécriture d'URL)*
> 2) a2enmod deflate *(gestion de compression pour la mise en cache des pages)*
> 3) a2enmod headers *(pour agir sur les en-têtes HTTP)*
> 4) a2enmod ssl *(pour gérer les certificats SSL et donc utiliser HTTPS)*

### Redémarrage d'apache2.
> 1) systemctl restart apache2

### Installation d'apache2-utils pour l'authentification basique.
> 1) apt-get install -y apache2-utils

## Installation de PHP.
Maintenant qu'Apache est installé nous pouvons passer à l'installation de PHP.  
PHP est un langage de scripts généraliste et Open Source, spécialement conçu pour le développement d'applications web. Il peut être intégré facilement au HTML.  

### Installation du paquet php et de paquets complémentaires.
> 1) apt-get install -y php
> 2) apt-get install -y php-pdo php-mysql php-zip php-gd php-mbstring php-curl php-xml php-pear php-bcmath

### Création d'un fichier phpinfo.php à la racine du site (pour vérifier que PHP est actif).
> 1) nano /var/www/html/phpinfo.php
> **Saisir le code suivant à l'intérieur :** *lien à rentrer*

## Installation de MySQL/MariaDB.
Maintenant que PHP est installé nous pouvons passer à l'installation de MariaDB.  
MariaDB est un système de gestion de base de données édité sous licence GPL.  

### Installation du paquet mariadb-server et sécurisation.
> 1) apt-get install -y mariadb-server
> 2) mariadb-secure-installation *(dire oui à tout)*

## Ouvrir mariadb et le redémarrer.
> 1) mariadb
> 2)systemctl restart mariadb

***Voilà !** Notre serveur LAMP est désormais installé. Il est maintenant possible de passer à l'installation de Wordpress.
*lien a mettre*
