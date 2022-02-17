**Tutto quello che segue è per un ambiente locale di sviluppo**

# Raspberry Pi 3 B+ come server web locale
## Sicurezza
### Cambiare password agli utenti pi e root
```
sudo passwd pi
sudo passwd root
```
### Creare un nuovo utente *nomeutente*
```
sudo adduser nomeutente
```
### Creare un nuovo gruppo *nomegruppossh* e aggiungere *nomeutente* e/o l'utente *pi*
```
sudo groupadd nomegruppossh
sudo adduser nomeutente nomegruppossh
```
### Abilitare SSH e consentire l'accesso per il solo gruppo *nomegruppossh*
Da Menu > Preferenze > Raspberry Pi Configuration > Interfaces > SSH: Enable

Abilitare l'accesso per il solo gruppo *nomegruppossh*
Aggiungere al file /etc/ssh/sshd_config la riga
```
AllowGroups nomegruppossh
```
Far ripartire il servizio ssh
```
sudo systemctl restart ssh
```
## Disinstallare pacchetti non necessari
Disinstallare pacchetti non necessari da Menu > Preferenze > Add/Remove Software

## Aggiornare il sistema
```
sudo apt update
sudo apt upgrade
sudo apt update
sudo apt-get install clamav clamav-docs -y
```
## Installare LAMP
```
sudo apt install apache2 -y
sudo chown -R nomeutente:www-data /var/www/html/
sudo chmod -R 770 /var/www/html/
sudo apt install php php-mbstring mysql-server php-mysql -y
