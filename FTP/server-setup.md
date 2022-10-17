# Installer un service FTP sous Debian 11

## Installation de vsftpd.
sudo apt install vsftpd -y

## Exécution de vsftpd.
sudo systemctl start vsftpd
sudo systemctl status vsftpd
systemctl enable vsftpd.service

## Ajout d’un nouvel utilisateur au système puis ajout à la configuration du programme.
sudo adduser nomdutilisateur
echo "nomdutilisateur" | sudo tee -a /etc/vsftpd.userlist

## Création d’un répertoire pour les fichiers des utilisateurs.
sudo mkdir -p /home/nomdutilisateur/ftp_directory
sudo chown nobody:nogroup /home/nomdutilisateur/ftp_directory
sudo chmod a-w /home/nomdutilisateur/ftp_directory
sudo mkdir -p /home/nomdutilisateur/ftp_directory/ftp_data
sudo chown nomdutilisateur:nomdutilisateur /home/nomdutilisateur/ftp_directory/ftp_data
cd /home/nomdutilisateur/ftp_directory/
chmod -R 777 ftp_data

## Sauvegarde du fichier de configuration ftp.
sudo cp /etc/vsftpd.conf /etc/vsftpd.conf.bak

## Édition du fichier.
nano /etc/vsftpd.conf
À mettre dans le fichier (copier le contenu du lien) : https://github.com/rvHoney/linux-setup-cheatsheet/FTP/vsftpd.conf/                                                                                                                                                                                                                                                                                                                                                                                

## Rechargement du serveur et vérification du service
sudo systemctl restart vsftpd
sudo systemctl status vsftpd

## /!\ SI IL EST IMPOSSIBLE DE SE CONNECTER ET QUE L’ERREUR SUIVANTE APPARAIT “500 OOPS: vsftpd: refusing to run with writable root inside chroot()” /!\

## Ajouter allow_writeable_chroot=YES à /etc/vsftpd/vsftpd.conf

nano /etc/vsftpd.conf
allow_writeable_chroot=YES
service vsftpd restart
