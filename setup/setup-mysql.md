## Installare MySQL

```
sudo apt install mysql-server -y
```

oppure

```
sudo apt install mariadb-server -y
```

Configurazione di sicurezza post installazione:

```
sudo mysql_secure_installation
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


## Creare un DB e uno user ad-hoc

```
sudo mysql
CREATE DATABASE nome_db;
GRANT ALL PRIVILEGES ON nome_db.* TO 'nome_user'@'localhost' IDENTIFIED BY 'user_password';
GRANT ALL PRIVILEGES ON nome_db.* TO 'nome_user'@'%' IDENTIFIED BY 'user_password';
FLUSH PRIVILEGES;
exit
```


## Configurare MySQL per ????????????????????????????

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
