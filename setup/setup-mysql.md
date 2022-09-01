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
