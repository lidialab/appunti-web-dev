# Raspberry Pi OS 64 bit - port of Debian Bullseye

Con i seguenti parametri preimpostati (utilizzando Raspberry Pi Imager):
- Hostname
- Password di pi
- SSH abilitato
- Time zone di Roma
- keyboard layout IT
- Telemetria disabilitata

## Post avvio

```
sudo apt update && sudo apt upgrade -y
sudo reboot
```

## LAMP server

```
sudo apt install apache2 mariadb-server php libapache2-mod-php php-mysql -y
sudo mysql_secure_installation
apache2ctl -t
sudo nano /etc/apache2/apache2.conf     # aggiunto ServerName
sudo apt install phpmyadmin -y
```

## Utenti e accessi remoti per MySQL / MariaDB
Creare un nuovo utente MariaDB e dare i privilegi di accesso anche da fuori localhost ai DB necessari (WP, NC, ...).

```
CREATE USER 'user';
GRANT ALL PRIVILEGES ON database.* TO 'user'@'type_of_access' IDENTIFIED BY 'password' WITH GRANT OPTION;
flush privileges;
```

## NextCloud
```
sudo apt install snapd
sudo snap install nextcloud
```



























