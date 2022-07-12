# Setup macchina virtuale Kubuntu per sviluppatori (VirtualBox Windows)

post installazione iso kubuntu

```
sudo apt update
sudo apt upgrade
sudo apt-get install clamav clamav-docs libclamunrar7 -y
```

## PHP, Composer, nodeJS

```
sudo apt install php -y
sudo apt install php7.2-curl -y   

php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');"
php -r "if (hash_file('SHA384', 'composer-setup.php') === '544e09ee996cdf60ece3804abc52599c22b1f40f4323403c44d44fdfdd586475ca9813a858088ffbc1f233e9b180f061') { echo 'Installer verified'; } else { echo 'Installer corrupt'; unlink('composer-setup.php'); } echo PHP_EOL;"
php composer-setup.php
php -r "unlink('composer-setup.php');"

sudo mv composer.phar /usr/local/bin/composer

sudo apt install curl -y

curl -sL https://deb.nodesource.com/setup_9.x | sudo -E bash -
sudo apt-get install -y nodejs

sudo apt-get install -y build-essential
sudo apt-get install -y network-manager libnss3-tools jq xsel -y
sudo apt-get install -y php7.2-cli php7.2-curl php7.2-mbstring  php7.2-xml php7.2-zip php7.2-sqlite3 php7.2-mysql php7.2-pgsql -y
```
### Riferimenti
Composer: https://getcomposer.org/

### Note
okkio alla versione php 7.2 --> X.x

## Valet

```
composer global require cpriego/valet-linux

export PATH=$PATH:/home/lidia/.config/composer/vendor/bin/

sudo /etc/init.d/apache2 stop
sudo apt-get remove apache2
valet install

valet domain vmlab
mkdir sviluppo
cd sviluppo/
valet park
```
### Sottodomini:
mkdir sottocartella
extensione/sottocartella --> http://sottocartella.extensione
http://sottocartella.extensione --> extensione/sottocartella

#### https:
valet secure sottocartella --> https://sottocartella.dev

## MariaDB

```
sudo apt-get install mariadb-client-10.1 mariadb-server-10.1 mariadb-server -y

sudo mysql -uroot
> use mysql;
> update user set plugin='' where User='root';
> flush privileges;
> exit
```

## WordPress e WP-CLI

```
curl -O https://raw.githubusercontent.com/wp-cli/builds/gh-pages/phar/wp-cli.phar
php wp-cli.phar --info
chmod +x wp-cli.phar
sudo mv wp-cli.phar /usr/local/bin/wp

mkdir wpkit; cd wpkit; wp core download --locale=it_IT
```
## phpMyAdmin
Vedi phpmyadmin.md

### Riferimenti
https://www.phpmyadmin.net/
https://docs.phpmyadmin.net/en/latest/

## GIT

## Konsole
Creare un nuovo profilo dal menu Impostazioni di Konsole e poi impostarlo come profilo predefinito di Konsole
Per personalizzare il prompt fare riferimento a 
http://guide.debianizzati.org/index.php/Colorare_bash
http://www.pluto.it/files/ildp/HOWTO/Bash-Prompt-HOWTO/Bash-Prompt-HOWTO-2.html
e modificare la variabile PS1 nel file .bashrc della propria home

## Atom.io

## Sublime Text 3
https://www.sublimetext.com/docs/3/linux_repositories.html
```
sudo wget -qO - https://download.sublimetext.com/sublimehq-pub.gpg | sudo apt-key add -
sudo apt-get install apt-transport-https
echo "deb https://download.sublimetext.com/ apt/stable/" | sudo tee /etc/apt/sources.list.d/sublime-text.list
sudo apt-get update
sudo apt-get install sublime-text
```
