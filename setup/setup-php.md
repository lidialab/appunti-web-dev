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

### Installare phpMyAdmin

[[setup-phpmyadmin]]


### php.ini

max_execution_time

upload_max_filesize

memory_limit

post_max_size
 
post_max_size > upload_max_filesize