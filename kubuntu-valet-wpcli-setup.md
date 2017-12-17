Appunti tratti dalle super lezioni di [Alecaddd](https://www.youtube.com/watch?v=zu42YzJ8_OM&list=PLriKzYyLb28l4vbFOrb0wIr11Iguj4Ur1 "Pop!_OS Development Setup")

```
sudo apt install -y php curl php7.1-curl

php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');"
php -r "if (hash_file('SHA384', 'composer-setup.php') === '544e09ee996cdf60ece3804abc52599c22b1f40f4323403c44d44fdfdd586475ca9813a858088ffbc1f233e9b180f061') { echo 'Installer verified'; } else { echo 'Installer corrupt'; unlink('composer-setup.php'); } echo PHP_EOL;"
php composer-setup.php
php -r "unlink('composer-setup.php');"


curl -sL https://deb.nodesource.com/setup_9.x | sudo -E bash -
sudo apt-get install -y nodejs build-essential

sudo mv composer.phar /usr/local/bin/composer

composer global require cpriego/valet-linux
export PATH=$PATH:/home/lidia/.config/composer/vendor/bin/
sudo apt-get install -y network-manager libnss3-tools jq xsel
sudo apt-get install -y php7.1-cli php7.1-curl php7.1-mbstring php7.1-mcrypt php7.1-xml php7.1-zip php7.1-sqlite3 php7.1-mysql php7.1-pgsql
sudo /etc/init.d/apache2 stop
sudo apt-get remove apache2
valet install

valet domain dev
mkdir sviluppo
cd sviluppo/
valet park
mkdir sottocartella
http://sottocartella.dev --> localhost/sottocartella

valet secure sottocartella --> https://sottocartella.dev

sudo apt-get install -y mariadb-client-10.1 mariadb-server-10.1 mariadb-server
 
sudo mysql -uroot
> use mysql;
> update user set plugin='' where User='root';
> flush privileges;

curl -O https://raw.githubusercontent.com/wp-cli/builds/gh-pages/phar/wp-cli.phar
php wp-cli.phar --info
chmod +x wp-cli.phar
sudo mv wp-cli.phar /usr/local/bin/wp

mkdir wpkit
cd wpkit
wp core download --locale=it_IT

phpMyAdmin
config.inc.php
$cfg['Servers'][$i]['AllowNoPassword'] = true;

crea nuovo db

aggiorna file wp-config.php
```
