# Preparare l'ambiente di sviluppo in locale per WordPress (s.o. Debian based)

Appunti tratti dalle super lezioni della serie [Pop!_OS Development Setup](https://www.youtube.com/watch?v=zu42YzJ8_OM&list=PLriKzYyLb28l4vbFOrb0wIr11Iguj4Ur1 "Pop!_OS Development Setup") di [Alecaddd](https://github.com/Alecaddd)

NB: configurazione provata su un'installazione fresh (fisica e virtuale) di una distro Debian based (ubuntu, kubuntu, pop! os, os elementary; sempre sulla versione più recente), attenzione alla versione php (adattare php7.1 alla versione scaricabile --> phpX.y):

## PHP e COMPOSER - Installazione
```
sudo apt-get install -y php curl php7.1-curl

php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');"
php -r "if (hash_file('SHA384', 'composer-setup.php') === '544e09ee996cdf60ece3804abc52599c22b1f40f4323403c44d44fdfdd586475ca9813a858088ffbc1f233e9b180f061') { echo 'Installer verified'; } else { echo 'Installer corrupt'; unlink('composer-setup.php'); } echo PHP_EOL;"
php composer-setup.php
php -r "unlink('composer-setup.php');"


curl -sL https://deb.nodesource.com/setup_9.x | sudo -E bash -
sudo apt-get install -y nodejs build-essential

sudo mv composer.phar /usr/local/bin/composer
```
## Valet - Installazione
```
composer global require cpriego/valet-linux
export PATH=$PATH:/home/lidia/.config/composer/vendor/bin/
sudo apt-get install -y network-manager libnss3-tools jq xsel
sudo apt-get install -y php7.1-cli php7.1-curl php7.1-mbstring php7.1-mcrypt php7.1-xml php7.1-zip php7.1-sqlite3 php7.1-mysql php7.1-pgsql
sudo /etc/init.d/apache2 stop
sudo apt-get remove apache2
valet install
```
## Valet - Impostare cartella dei progetti
```
valet domain estensione
mkdir sviluppo
cd sviluppo/
valet park
mkdir sottocartella
http://sottocartella.estensione --> localhost/sottocartella

valet secure sottocartella --> https://sottocartella.estensione
```
NB: evitare estensione .dev

## DATABASE (MariaDB)
```
sudo apt-get install -y mariadb-client-10.1 mariadb-server-10.1 mariadb-server
 
sudo mysql -uroot
> use mysql;
> update user set plugin='' where User='root';
> flush privileges;
```
## WP CLI - Installazione
```
curl -O https://raw.githubusercontent.com/wp-cli/builds/gh-pages/phar/wp-cli.phar
php wp-cli.phar --info
chmod +x wp-cli.phar
sudo mv wp-cli.phar /usr/local/bin/wp

```
## phpMyAdmin
scaricare e scompattare nella cartella phpmyadmin del park Valet così diventerà raggiungibile qui --> http://phpmyadmin.estensione
se l'utente del database non ha password modificare nel file config.inc.php la linea:
```
$cfg['Servers'][$i]['AllowNoPassword'] = true;
```
## WP CLI - Installare una nuova istanza di WordPress
```
crea nuovo db wpkit
mkdir wpkit
cd wpkit
wp core download --locale=it_IT
aggiornare il file wp-config.php con i dati del db
http://wpkit.estensione
```
## NPM (versione LTS raccomandata)
```
curl -sL https://deb.nodesource.com/setup_8.x | sudo -E bash -
sudo apt-get install -y nodejs
sudo apt-get install -y build-essential
```
## NPM (versione 10...)
```
curl -sL https://deb.nodesource.com/setup_10.x | sudo -E bash -
sudo apt-get install -y nodejs
sudo apt-get install -y build-essential
```
## RUBY
```
sudo apt-get install -y ruby ruby-dev
```
## GRUNT CLI (globally)
```
sudo npm install -g grunt-cli
```
## SASS compiler (ruby)
```
sudo gem install sass
```
## SASS compiling task (per la directory del progetto)
```
sudo npm install grunt-contribut-sass --save-dev
sudo npm install grunt-contribut-watch --save-dev
```
## Esempio di file Gruntfile.js per compilazione Sass 
```
module.exports = function(grunt) {
   grunt.initConfig({
      pkg: grunt.file.readJSON('package.json'),

      sass:{
         dev: {
            options: {
               style: 'expanded',
               sourcemap: 'none',
            },
            files: {
               'stileLL.css': 'scss/stileLL.scss'
            }
         }
      },

      watch: {
         css: {
            files: '**/*.scss',
            tasks: ['sass']
         }
      },
   });

   grunt.loadNpmTasks('grunt-contrib-sass');
   grunt.loadNpmTasks('grunt-contrib-watch');
   grunt.registerTask('default',['watch']);
}
```
## Esempio di file package.json per compilazione Sass 
```
{
  "name": "sitostatico",
  "version": "1.0.0",
  "description": "Progetto base per studio css",
  "main": "index.html",
  "author": "LidiaLAB",
  "dependencies": {},
  "devDependencies": {
    "grunt": "^1.0.3",
    "grunt-contrib-sass": "^1.0.0",
    "grunt-contrib-watch": "^1.1.0"
  }
}
```
## PS
Per raggiungere l'ambiente di sviluppo da un'altra postazione aggiungere le mappature dns nel file hosts del s.o. in uso.
