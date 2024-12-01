# Macchina Virtuale su VirtualBox
Ubuntu Server 22.04.1 LTS 64:
4GB RAM - disco virtuale allocato dinamicamente (un po' più lento), VDI (VBox), 30GB - 2 CPU, rete con Bridge. 

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


--------------------------------------------------------------------------------------------------------------------
## CERTBOT
sudo apt install certbot python3-certbot-apache -y
