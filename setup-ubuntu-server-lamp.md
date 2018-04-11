```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install -y build-essential virtualbox-dkms nano zip unzip curl man-db acpid git module-assistant
sudo reboot
sudo mount /dev/cdrom /media/cdrom
sudo m-a prepare
sudo sh /media/cdrom/VBoxLinuxAdditions.run  --nox11
sudo reboot
sudo usermod -a -G vboxsf nomeutente
logout (nomeutente)
login  (nomeutente)
sudo usermod -a -G vboxsf www-data
preparare vboxsf.conf per /sites-available/
sudoedit ports.conf per aggiungere Listen 8080

sudo a2ensite vboxsf
sudo a2dissite 000-default
sudo a2enmod rewrite vhost_alias
sudo service apache2 restart

sudoedit /etc/php/7.1/mods-available/phpcustom.ini
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

sudo phpenmod phpcustomphpquery -v 7.1 -s apache2 -M
sudo touch /var/log/php_errors.log
sudo chown www-data: /var/log/php_errors.log

sudo apt-get install php-mcrypt php-intl php-sqlite3 php-mbstring php-xml php-gd -y
sudo phpenmod mbstring simplexml

/etc/apache2/apache2.conf
```
Per correggere problemi Virtual Box Linux Additions provare:
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install -y build-essential virtualbox-dkms nano zip unzip curl man-db acpid git module-assistant
sudo reboot
sudo mount /dev/cdrom /media/cdrom
sudo m-a prepare
sudo sh /media/cdrom/VBoxLinuxAdditions.run  --nox11
sudo reboot
```
