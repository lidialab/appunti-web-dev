# VIRTUAL BOX

Salvato qui da un altro file, Tutto da verificare.
  
?????????????????????????????????????????????????????  

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
