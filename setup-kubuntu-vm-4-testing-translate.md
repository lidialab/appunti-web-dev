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

CREATE DATABASE wpt;
USE wpt;
CREATE USER 'root@%' IDENTIFIED BY 'root';
GRANT ALL ON wpt.* TO 'root@%';
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



``

