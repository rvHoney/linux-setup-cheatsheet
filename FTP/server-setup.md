# Installer un service FTP sous Debian 11

## Installation de vsftpd.
1) sudo apt install vsftpd -y

## Exécution de vsftpd.
1) sudo systemctl start vsftpd
2) sudo systemctl status vsftpd
3) systemctl enable vsftpd.service

## Ajout d’un nouvel utilisateur au système puis ajout à la configuration du programme.
1) sudo adduser nomdutilisateur
2) echo "nomdutilisateur" | sudo tee -a /etc/vsftpd.userlist

## Création d’un répertoire pour les fichiers des utilisateurs.
### /!\ Le texte en gras est à modifier /!\
1) sudo mkdir -p /home/**nomdutilisateur**/ftp_directory
2) sudo chown nobody:nogroup /home/**nomdutilisateur**/ftp_directory
3) sudo chmod a-w /home/**nomdutilisateur**/ftp_directory
4) sudo mkdir -p /home/**nomdutilisateur**/ftp_directory/ftp_data
5) sudo chown **nomdutilisateur**:**nomdutilisateur** /home/**nomdutilisateur**/ftp_directory/ftp_data
6) cd /home/**nomdutilisateur**/ftp_directory/
7) chmod -R 777 ftp_data

## Sauvegarde du fichier de configuration ftp.
1) sudo cp /etc/vsftpd.conf /etc/vsftpd.conf.bak

## Édition du fichier.
1) nano /etc/vsftpd.conf
2) À mettre dans le fichier (*copier le contenu du lien*) : https://github.com/rvHoney/linux-setup-cheatsheet/blob/main/FTP/vsftpd.conf

## Rechargement du serveur et vérification du service
5) sudo systemctl restart vsftpd
6) sudo systemctl status vsftpd

## /!\ SI IL EST IMPOSSIBLE DE SE CONNECTER ET QUE L’ERREUR SUIVANTE APPARAIT “500 OOPS: vsftpd: refusing to run with writable root inside chroot()” /!\

## Ajouter allow_writeable_chroot=YES à /etc/vsftpd/vsftpd.conf

1) nano /etc/vsftpd.conf
2) allow_writeable_chroot=YES
3) service vsftpd restart
