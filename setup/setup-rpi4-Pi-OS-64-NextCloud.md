# Raspberry Pi OS 64 bit - port of Debian Bullseye

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
CREATE DATABASE nome_database;
CREATE USER 'nome_utente';
GRANT ALL PRIVILEGES ON database.* TO 'nome_utente'@'accesso' IDENTIFIED BY 'password' WITH GRANT OPTION;
FLUSH PRIVILEGES;
exit
```

## NextCloud
```
cd /var/www/html/
sudo wget https://download.nextcloud.com/server/releases/latest-xx.zip
sudo unzip latest-xx.zip
sudo chown -R www-data:www-data /var/www/html/nextcloud/

cd /etc/apache2/sites-available/
sudoedit nextcloud.conf

<VirtualHost *:80>
     DocumentRoot "/var/www/html/nextcloud"
     ServerName nextcloud

     <Directory "/var/www/html/nextcloud/">
         Options MultiViews FollowSymlinks
         AllowOverride All
         Order allow,deny
         Allow from all
    </Directory>

    TransferLog /var/log/apache2/nextcloud_access.log
    ErrorLog /var/log/apache2/nextcloud_error.log
</VirtualHost>

sudo a2ensite nextcloud.conf
[*]sudo a2dissite 000-default.conf
apache2ctl -t
sudo systemctl restart apache2
```

sudoedit /etc/php/x.x/apache2/php.ini

```
post_max_size = 1024M
upload_max_filesize = 1024M
memory_limit = 512M
max_execution_time = 360
date.timezone = Europe/Rome
opcache.enable=1
opcache.interned_strings_buffer=8
opcache.max_accelerated_files=10000
opcache.memory_consumption=128
opcache.save_comments=1
opcache.revalidate_freq=1
 
```

Riavviare A2 (prima fai un check)

```
apache2ctl -t
sudo systemctl restart apache2
```

Abilitare la memoria cache

```
sudoedit /var/www/html/nextcloud/config/config.php

'memcache.local' => '\OC\Memcache\APCu',
```

Verificare la presenza dei seguenti moduli php

```
php -m | grep -i filter;
php -m | grep -i hash;
php -m | grep -i libxml;
php -m | grep -i openssl;
php -m | grep -i pcntl;
php -m | grep -i pdo_mysql;
php -m | grep -i session;
php -m | grep -i zlib;
```

Se necessario installare e attivare i seguenti moduli php

```
sudo apt -y install php-apcu;
sudo apt -y install php-bcmath;
sudo apt -y install php-bz2;
sudo apt -y install php-ctype;
sudo apt -y install php-curl;
sudo apt -y install php-dom;
sudo apt -y install php-exif;
sudo apt -y install php-fileinfo;
sudo apt -y install php-ftp;
sudo apt -y install php-gd;
sudo apt -y install php-gmp;
sudo apt -y install php-iconv;
sudo apt -y install php-imagick;
sudo apt -y install php-imap;
sudo apt -y install php-intl;
sudo apt -y install php-json;
sudo apt -y install php-mbstring;
sudo apt -y install php-memcached;
sudo apt -y install php-phar;
sudo apt -y install php-posix;
sudo apt -y install php-redis;
sudo apt -y install php-simplexml;
sudo apt -y install php-xmlreader;
sudo apt -y install php-xmlwriter;
sudo apt -y install php-zip;
```

## Verificare e/o disabilitare ssh per l'utente root

## Certificato SSL autogenerato
```
[*] sudo a2enmod ssl
sudo mkdir -p /etc/apache2/ssl
sudo openssl req -x509 -nodes -days 365 -newkey rsa:4096 -keyout /etc/apache2/ssl/apache.key -out /etc/apache2/ssl/apache.crt
sudoedit /etc/apache2/sites-available/default-ssl.conf

<VirtualHost *:443>
   ServerName your_domain_or_ip
   DocumentRoot /var/www/your_domain_or_ip

   SSLEngine on
   SSLCertificateFile /etc/apache2/ssl/apache.crt
   SSLCertificateKeyFile /etc/apache2/ssl/apache.key
</VirtualHost>

<VirtualHost *:80>
        ServerName nextcloud
        Redirect / https://nextcloud/
</VirtualHost>

sudo a2ensite default-ssl.conf
apache2ctl -t
sudo systemctl restart apache2
```
