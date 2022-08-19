# Raspberry Pi OS 64 bit - port of Debian Bullseye

Con i seguenti parametri preimpostati (utilizzando Raspberry Pi Imager):
- Hostname
- Password di pi
- SSH abilitato
- Time zone di Roma
- keyboard layout IT
- Telemetria disabilitata

## Post avvio

```
sudo apt update && sudo apt upgrade -y
sudo apt dist-upgrade
sudo apt autoremove
sudo reboot
```

Se necessario cambiare nome computer e aggiungerlo come localhost

```
sudoedit /etc/hostname
sudoedit /etc/hosts
sudo reboot
```

## LAMP server

```
sudo apt install apache2 php libapache2-mod-php php-apcu php-bcmath php-cli php-common php-curl php-gd php-gmp php-imagick php-intl php-mbstring php-mysql php-zip php-xml mariadb-server unzip -y
systemctl status apache2
systemctl status mariadb
[*] sudo systemctl start apache2
[*] sudo systemctl start mariadb
sudo phpenmod bcmath gmp imagick intl
sudo a2enmod dir env headers mime rewrite ssl
apache2ctl -t
[*] sudo nano /etc/apache2/apache2.conf     # aggiunto ServerName nome_tuo_server
sudo systemctl restart apache2
sudo mysql_secure_installation
sudo apt install phpmyadmin -y
```

```[*]: eseguire solo se necessario```

## Utenti e accessi remoti per MySQL / MariaDB
Creare un nuovo utente MariaDB e dare i privilegi di accesso anche da fuori localhost ai DB necessari (WP, NC, ...).

```
sudo mariadb
CREATE DATABASE nextcloud;
CREATE USER 'user';
GRANT ALL PRIVILEGES ON database.* TO 'user'@'type_of_access' IDENTIFIED BY 'password' WITH GRANT OPTION;
FLUSH PRIVILEGES;
EXIT
```

## NextCloud
```
sudo mkdir /var/www/html/nextcloud
cd nextcloud/
sudo wget https://download.nextcloud.com/server/installer/setup-nextcloud.php
sudo chgrp -R www-data /var/www/html/nextcloud/
sudo chown -R www-data /var/www/html/nextcloud/
cd /etc/apache2/sites-available/
sudo cp 000-default.conf 001-nextcloud.conf
sudoedit 001-nextcloud.conf

<VirtualHost *:80>
  ServerName tuonomeservizio.tuoserver
  ServerAlias www.tuonomeservizio.tuoserver
  DocumentRoot "/var/www/html/nextcloud"
</VirtualHost>

sudo a2ensite 001-nextcloud.conf
sudo a2enmod rewrite
sudo systemctl reload apache2
```

php.ini
```
post_max_size = 1024M
upload_max_filesize = 1024M
```




## Verificare e/o disabilitare ssh per l'utente root


