# Macchina Virtuale su VirtualBox
Ubuntu Server 22.04.1 LTS 64:
4GB RAM - disco virtuale allocato dinamicamente (un po' più lento), VDI (VBox), 30GB - 2 CPU, rete con Bridge. 


## Installare Apache

```
sudo apt update && sudo apt upgrade -y
sudo reboot
sudo apt install apache2 -y
sudo service apache2 status
# se non è attivo farlo partire con:
# sudo service apache2 start
```

### Verificare se il firewall è attivo:
```
sudo ufw status
```
Se è attivo verifica le app che possono essere raggiunte
```
sudo ufw app list
```
ed eventualmente abilita le porte 80 e 443 (ambiente di test)
```
sudo ufw allow http
sudo ufw allow https
```

### Verificare i file di configurazione di Apache
```
apachectl configtest
```

Se l'esito riporta messaggi diversi da "Syntax OK" risolvere.

Per "AH00558: apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1. Set the 'ServerName' directive globally to suppress this message"

Aggiungere la direttiva globale al file "apache2.conf"
```
sudo nano /etc/apache2/apache2.conf
```

in una delle seguenti forme:
```
ServerName "myserver.ext"
ServerName "IP_del_SERVER"
```
Ricontrollare con ```apachectl configtest```

Riavviare Apache
```
sudo systemctl reload apache2
```

## Installare MySQL
```
sudo apt install mysql-server -y
```

## Installare PHP
```
sudo apt install php libapache2-mod-php php-mysql -y
```

### Verificare il funzionamento di PHP in Apache
```
sudo mkdir /var/www/html/test
sudo nano /var/www/html/test/info.php
# contenuto del file info.php
<?php phpinfo() ?>
```

## Installare phpMyAdmin
```
sudo apt install phpmyadmin -y
```

----------------------------------------------------------------------------------------------------------------

oppure Scaricare phpmyadmin e scompattarlo in una sottocartella di www

### Utente phpmyadmin
Entrare nella console mysql e creare un utente ad hoc per phpmyadmin
```
CREATE USER 'master'@'%' IDENTIFIED BY 'master';
GRANT ALL PRIVILEGES ON *.* TO 'master'@'%' WITH GRANT OPTION;
flush privileges;
```

# Configurare MySQL
```
sudoedit /etc/mysql.conf
```
File mysql.conf
```
!includedir /etc/mysql/conf.d/
!includedir /etc/mysql/mysql.conf.d/

[mysqld]
collation-server = utf8_unicode_ci
character-set-server = utf8
bind-address = 0.0.0.0
slow_query_log = 1
slow_query_log_file = /var/log/mysql/slow.log
long_query_time = 2
```
Riavviamo MySQL
```
sudo service mysql restart
sudo chgrp adm /var/log/mysql/slow.log
```

# Mailcatcher
```
sudo apt install libsqlite3-dev ruby-dev -y
sudo gem install mailcatcher
sudoedit /lib/systemd/system/mailcatcher.service
```
File mailcatcher.service:
```
[Unit]
Description=MailCatcher Service

[Service]
Type=simple
ExecStart=/usr/local/bin/mailcatcher --foreground --ip 0.0.0.0

[Install]
WantedBy=multi-user.target
```
Lo avviamo e impostiamo che parta in automatico ad ogni reboot
```
sudo service mailcatcher start
sudo systemctl enable mailcatcher.service

sudoedit /etc/php/7.2/mods-available/mailcatcher.ini
```
File mailcatcher.ini:
```
sendmail_path = /usr/local/bin/catchmail
sendmail_from = mailcatcher@nomeserver.mydev
```
Avviamo mailcatcher
```
sudo phpenmod mailcatcher
sudo service apache2 start
```
Mailcatcher raggiungibile a: http://nomeserver.mydev:1080/



--------------------------------------------------------------------------------------------------------------------
VIRTUAL BOX:



Installiamo sw mancante (nano, zip, unzip, curl, man-db, acpid, git,...) e quello necessario per le V.Box G.Additions (build-essential, virtualbox-dkms, module-assistant)
```
sudo apt install -y build-essential virtualbox-dkms nano zip unzip curl man-db acpid git module-assistant gcc make perl
sudo apt install sendmail-bin -y
sudo reboot
sudo mkdir /media/cdrom
sudo mount /dev/cdrom /media/cdrom
sudo sh /media/cdrom/VBoxLinuxAdditions.run  --nox11
sudo reboot
```
verificare che le vb-ga siano funzionanti, in particolare il modulo per la condivisione delle cartelle
```
lsmod | grep vbox
lsmod | grep vboxsf
```
diamo i permessi necessari
```
sudo usermod -a -G vboxsf nomeutente
logout (nomeutente)
login  (nomeutente)
sudo usermod -a -G vboxsf www-data
```
preparare vboxsf.conf per /sites-available/
```
<VirtualHost *:80 *:8080>
  ServerName nomeserver
  ServerAlias *.mydev

  LogLevel info
  ErrorLog ${APACHE_LOG_DIR}/vboxsf-error.log
  CustomLog ${APACHE_LOG_DIR}/vboxsf-access.log combined

  RewriteEngine On

  <Directory />
    Options FollowSymLinks
    AllowOverride All
  </Directory>

  <Directory /media/>
    Order allow,deny
    Allow from all
    Require all granted
  </Directory>

  <Location /server-status>
    SetHandler server-status
    Order allow,deny
    Allow from all
    Require all granted
  </Location>

  UseCanonicalName Off
  VirtualDocumentRoot /media/sf_nomecartellacondivisa
</VirtualHost>
```

```
sudo a2ensite vboxsf
sudo a2dissite 000-default
sudo a2enmod rewrite vhost_alias
sudo service apache2 restart
```

```
sudoedit /etc/php/7.2/mods-available/phpcustom.ini
; Custom shared config
; priority=01
error_reporting=E_ALL
display_errors=On
display_startup_errors=On
error_log=/var/log/php_errors.log
log_errors_max_len=0
memory_limit=256M
post_max_size=100M
upload_max_filesize=100M

sudo phpenmod phpcustom
phpquery -v 7.2 -s apache2 -M
sudo touch /var/log/php_errors.log
sudo chown www-data: /var/log/php_errors.log

sudo apt install php-mcrypt php-intl php-sqlite3 php-mbstring php-xml php-gd -y
sudo phpenmod mbstring simplexml

/etc/apache2/apache2.conf
```



# Troubleshooting
Per correggere problemi Virtual Box Linux Additions provare:
```
sudo apt update
sudo apt upgrade -y
sudo reboot
sudo mount /dev/cdrom /media/cdrom
sudo m-a prepare
sudo sh /media/cdrom/VBoxLinuxAdditions.run  --nox11
sudo reboot
```
