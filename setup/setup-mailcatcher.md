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

sudoedit /etc/php/x.x/mods-available/mailcatcher.ini
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

