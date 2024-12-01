# phpMyAdmin

## Installare phpMyAdmin

### Manualmente

```
cd /var/www/html/
sudo wget https://www.phpmyadmin.net/downloads/phpMyAdmin-latest-all-languages.zip
sudo unzip phpMyAdmin-latest-all-languages.zip
sudo rm phpMyAdmin-latest-all-languages.zip -R
sudo mv phpMyAdmin-x.x.x-all-languages/ phpmyadmin
```

### Installare phpMyAdmin in una distro Debian

Scaricare phpmyadmin e scompattarlo nella directory del localhost oppure eseguire:

```
sudo apt install phpmyadmin -y
sudo ln -s /usr/share/phpmyadmin/ /var/www/html/phpmyadmin
sudo service apache2 restart
```

### Creare un utente per lo sviluppo

Entrare nella console mysql

```
sudo mysql
```

Creare un utente

```
CREATE USER 'master'@'%' IDENTIFIED BY 'master';
GRANT ALL PRIVILEGES ON *.* TO 'master'@'%' WITH GRANT OPTION;
flush privileges;
```

### Parametri

config.inc.php

```
$cfg['Servers'][$i]['AllowNoPassword'] = true;
$cfg['blowfish_secret'] = 'abcdefghil1234567890£$%&/(@#ù+12'; /* deve essere alemno 32 chars */
```

### Tema phpMyAdmin, migliorare la dimensione carattere per le istruzioni SQL

duplicare la cartella del tema pmahomme in phpMyAdmin/themes

nella nuova cartella editare il file info.inc.php oppure theme.json (dipende dalla versione) e cambiare nome e versione del tema

nella sottocartella css editare il file codemirror.css.php e aggiungere alla fine del file le seguenti regole css sostituendo la dimensione del font con quella più adatta

```
.CodeMirror pre, .CodeMirror textarea {
   font-size: 20px;
}
```

Dalla home di phpMyAdmin cambiare il tema e verificare che tutto sia visualizzato correttamente
