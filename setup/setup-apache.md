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
sudo ufw allow http 80/tcp
sudo ufw allow https 443/tcp
```

che può anche essere scritto:

```
sudo ufw allow http
sudo ufw allow https
```

abilitare ufw:

```
sudo ufw enable
```

far ripartire ufw per rendere operative le nuove regole:

```
sudo ufw reload
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

Nella directory /etc/apache2/sites-available creare un file $DOMAIN.conf per il nuovo sito.
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
  ServerName $DOMAIN
  ServerAlias www.$DOMAIN
  DocumentRoot "/var/www/html/$DOMAIN"

  <Directory /var/www/html/$DOMAIN>
        AllowOverride All
        Require all granted
  </Directory>

  ErrorLog \${APACHE_LOG_DIR}/error-$DOMAIN.log
  CustomLog \${APACHE_LOG_DIR}/access-$DOMAIN.log combined

</VirtualHost>
```

Abilitare il sito e riavviare apache:

```
sudo a2ensite $DOMAIN.conf
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

## .htaccess

Va abilitato per ogni singolo virtual host con la seguente direttiva:

```
<Directory /var/www/html/nome_directory>
        AllowOverride All
</Directory>
```
## prettylink

```
sudo a2enmod rewrite
sudo systemctl reload apache2

```
