# Nextcloud

## Prerequisiti

### hostname
[Dare un hostname qualificato al server](setup-hostname-debian.md) "Dare un hostname qualificato al server"

### AMP server

- [Apache2](setup-apache.md)
- [MySQL o MariaDB](setup-mysql.md)
- [PHP](setup-php.md)


#### Pacchetti PHP di supporto

Verificare la presenza di tutti i moduli php obbligatori.

```
sudo apt install php-apcu php-bcmath php-cli php-common php-curl php-gd php-gmp php-imagick php-intl php-mbstring php-mysql php-zip php-xml

sudo phpenmod bcmath gmp imagick intl
```

#### Pacchetti app di supporto
```
sudo apt install libmagickcore-6.q16-6-extra unzip -y
```

## Installazione da script php
https://docs.nextcloud.com/server/24/admin_manual/installation/source_installation.html

Scaricare lo script php di inizializzazione https://download.nextcloud.com/server/installer/setup-nextcloud.php


## Installazione manuale

### Impostazioni Apache2

```
cd /var/www
sudo wget https://download.nextcloud.com/server/releases/latest.zip
unzip latest.zip
sudo chown -R www-data:www-data nextcloud.myhome.ext
sudo a2dissite 000-default.conf
sudo nano /etc/apache2/sites-available/nextcloud.myhome.ext.conf
```

```
<VirtualHost *:80>
    DocumentRoot "/var/www/nextcloud.myhome.ext"
    ServerName nextcloud.myhome.ext

    <Directory "/var/www/nextcloud.myhome.ext/">
        Options MultiViews FollowSymlinks
        AllowOverride All
        Order allow,deny
        Allow from all
   </Directory>

   TransferLog /var/log/apache2/nextcloud.myhome.ext_access.log
   ErrorLog /var/log/apache2/nextcloud.myhome.ext_error.log

</VirtualHost>
```

```
sudo a2ensite apache-config-file-name.conf
sudo a2enmod dir env headers mime rewrite ssl
sudo systemctl restart apache2
```

### Impostazioni PHP

/etc/php/x.x/apache2/php.ini

```
post_max_size = 1024M
upload_max_filesize = 1024M
max_execution_time = 360
post_max_size = 1024M
date.timezone = America/Detroit
opcache.enable=1
opcache.interned_strings_buffer=8
opcache.max_accelerated_files=10000
opcache.memory_consumption=128
opcache.save_comments=1
opcache.revalidate_freq=1
```

```
sudo systemctl restart apache2
```

### HTTPS certificato (per internet)
https://certbot.eff.org/instructions?ws=apache&os=ubuntufocal

```
sudo apt install snapd
sudo snap install core; sudo snap refresh core
sudo snap install --classic certbot
sudo ln -s /snap/bin/certbot /usr/bin/certbot
sudo certbot --apache
```


Nel file :

```
sudo vim /etc/apache2/sites-available/nextcloud.myhome.ext-le-ssl.conf
```

aggiungere dopo la riga "ServerName":

```
<IfModule mod_headers.c>
    Header always set Strict-Transport-Security "max-age=15552000; includeSubDomains"
</IfModule>
```

### HTTPS certificato (per intranet)

..................


### Perfezionamenti finali

```
sudo chmod 660 /var/www/<nextcloud_directory>/config/config.php
sudo chown root:www-data /var/www/<nextcloud_directory/config/config.php
sudo vim /var/www/nextcloud.myhome.ext/config/config.php
```

Aggiungere:

```
'memcache.local' => '\\OC\\Memcache\\APCu',
```

```
sudo vim /var/www/nextcloud.myhome.ext/config/config.php
```

Aggiungere:

```
'default_phone_region' => 'IT',
```




## Fonti

https://www.learnlinux.tv/nextcloud-full-setup-implementation-guide/
https://www.learnlinux.tv/build-an-awesome-nextcloud-server-updated-for-ubuntu-22-04/