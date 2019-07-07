# Macchina Virtuale su VirtualBox
Ubuntu Server LTS 64:
2GB RAM - disco virtuale allocato dinamicamente (un po' più lento), VDI (VBox), 10GB - 2 CPU, enable PAE/NX ; 
~Port forwarding~ non funziona, riprovare, per ora Bridge ; 
Cartella condivisa in auto-mount ; 
No audio ; 
SSH, autenticazione con chiavi cifrate
```
sudo apt-get update
sudo apt-get upgrade
sudo reboot
```
installiamo sw mancante (nano, zip, unzip, curl, man-db, acpid, git,...) e quello necessario per le V.Box G.Additions (build-essential, virtualbox-dkms, module-assistant)
```
sudo apt-get install -y build-essential virtualbox-dkms nano zip unzip curl man-db acpid git module-assistant gcc make perl
sudo apt-get install sendmail-bin -y
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
sudoedit ports.conf per aggiungere Listen 8080
```
sudo a2ensite vboxsf
sudo a2dissite 000-default
sudo a2enmod rewrite vhost_alias
sudo service apache2 restart
```
^ non ha funzionato
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

sudo apt-get install php-mcrypt php-intl php-sqlite3 php-mbstring php-xml php-gd -y
sudo phpenmod mbstring simplexml

/etc/apache2/apache2.conf
```
Mailcatcher
```
sudo apt-get install libsqlite3-dev ruby-dev -y
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
sendmail_from = mailcatcher@ubu1804.mydev
```
Avviamo mailcatcher
```
sudo phpenmod mailcatcher
sudo service apache2 start
```
Mailcatcher raggiungibile a: http://ubu1804.mydev:1080/

# Troubleshooting
Per correggere problemi Virtual Box Linux Additions provare:
```
sudo apt-get update
sudo apt-get upgrade
sudo reboot
sudo mount /dev/cdrom /media/cdrom
sudo m-a prepare
sudo sh /media/cdrom/VBoxLinuxAdditions.run  --nox11
sudo reboot
```
