kubuntu (lite installation)

from VM terminal:

``

sudo apt install net-tools -y

sudo apt install openssh-server -y

``

switch to a ssh connection from Windows Terminal (new PS shell).

``
sudo apt update

sudo apt upgrade -y

sudo apt install git curl apache2 ghostscript libapache2-mod-php mysql-server php php-bcmath php-curl php-imagick php-intl php-json php-mbstring php-mysql php-xml php-zip -y


sudo curl -O https://raw.githubusercontent.com/wp-cli/builds/gh-pages/phar/wp-cli.phar

sudo chmod +x wp-cli.phar

sudo mv wp-cli.phar /usr/local/bin/wp


cd /var/www/html/

sudo mkdir /var/www/html/wptranslate

sudo chmod 777 /var/www/html/wptranslate

cd wptranslate/

wp core download

sudo mysql -u root



CREATE DATABASE wordpress;

USE wordpress;

CREATE USER 'wordpress' IDENTIFIED BY 'password';

GRANT ALL ON wordpress.* TO 'wordpress';

FLUSH PRIVILEGES;

quit



cd /etc/apache2/sites-available/

sudo cp 000-default.conf wpt.conf


	<VirtualHost *:80>
		DocumentRoot /var/www/html/wptranslate
		<Directory /var/www/html/wptranslate>
			Options FollowSymLinks
			AllowOverride Limit Options FileInfo
			DirectoryIndex index.php
			Require all granted
		</Directory>
		<Directory /var/www/html/wptranslate/wp-content>
			Options FollowSymLinks
			Require all granted
		</Directory>
	</VirtualHost>



sudo a2ensite wpt.conf

sudo a2enmod rewrite

sudo systemctl reload apache2


cd /var/www/html/wptranslate

wp config create --dbname=wordpress --dbuser=wordpress --dbpass="password" --dbcharset=latin1 --dbcollate=latin1_swedish_ci

wp core install --url="wordpress.test" --title="Test Site" --admin_user=admin --admin_password="password" --admin_email=example@example.com


git clone https://github.com/WordPress/translate-w-org-env.git

cd translate-w-org-env

./provision.sh -t lamp -d /var/www/html/wptranslate/




``


codice

