# Macchina Virtuale su VirtualBox
Ubuntu Server 22.04.1 LTS 64:
4GB RAM - disco virtuale allocato dinamicamente (un po' più lento), VDI (VBox), 30GB - 2 CPU, rete con Bridge. 

## Installare Ubuntu server e aggiornare il sistema
[[setup-ubuntu-server.md]]

## Installare Apache

```
sudo apt install apache2 -y
sudo service apache2 status
# se non è attivo farlo partire con:
# sudo service apache2 start
# o
# sudo systemctl start apache2.service
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
# oppure
apache2ctl -t
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
Ricontrollare con ```apachectl -t```

Riavviare Apache
```
sudo systemctl reload apache2
```

### Apache VirtualHosts

### Creare un nuovo VHost

Nella directory /etc/apache2/sites-available creare un file .conf per il muovo sito.
Inserire i parametri minimi per ServerName e DocumentRoot come ad esempio:

```
<VirtualHost *:80>
  ServerName phptest.myext
  DocumentRoot "/var/www/html/test"
</VirtualHost>
```

Può essere aggiunto anche un Alias per gestire domini con e senza www:

```
<VirtualHost *:80>
  ServerName phptest.myext
  ServerAlias www.phptest.myext
  DocumentRoot "/var/www/html/test"
</VirtualHost>
```

Abilitare il sito e riavviare apache:

```
sudo a2ensite nomefile.conf
sudo systemctl reload apache2
```

Per verificare i VHosts creati eseguire:

```
apache2ctl -S
```

Creare la directory corrispondente, inserire gli asset del sito, assegnare la proprietà a www-data (utente e gruppo) esempio:

```
sudo mkdir /var/www/html/test
wget ...
unzip ...
sudo chgrp -R www-data /var/www/html/test  
sudo chown -R www-data /var/www/html/test
```

## Nel client che interrogherà il server creare le voci nel file hosts, esempio in Windows modificare il file \Windows\System32\drivers\etc\hosts aggiungendo:
```
192.168.10.222	localdev
192.168.10.222	phptest.myext
192.168.10.222	www.phptest.myext
```

dove con 192.168.10.222 si intende l'IP del vostro server locale Ubuntu.

## Installare MySQL
```
sudo apt install mysql-server -y
```

## Utilizzare utente root con password (ambiente di test)
```
sudo mysql
select user, host, authentication_string from mysql.user;
alter user root@localhost identified with mysql_native_password by 'root';
flush privileges;
exit
```
Per testare se funziona accedere con ```mysql -u root -p``` inserisci la password, se entri è ok (poi ```exit``` per uscire).


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

Scaricare phpmyadmin e scompattarlo in una sottocartella di www

# Mailcatcher
```
sudo apt install libsqlite3-dev ruby-dev gcc make -y
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
sendmail_from = mailcatcher@nomeserver.myext
```
Avviamo mailcatcher
```
sudo phpenmod mailcatcher
sudo service apache2 start
```
Mailcatcher raggiungibile a: http://nomeserver.mydev:1080/



--------------------------------------------------------------------------------------------------------------------

????????????????????????????

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
