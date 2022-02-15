WSL2 running on W10
MS Store
Ubuntu 20.04 LTS

```
sudo apt update; sudo apt upgrade -y

sudo apt-get install lamp-server^ -y
sudo apt install ghostscript php php-bcmath php-curl php-imagick php-intl php-json php-mbstring php-xml php-zip php-gd php-mbstring phpmyadmin -y
sudo ln -s /usr/share/phpmyadmin/ /var/www/html/phpmyadmin

sudo service apache2 start
service apache2 status
cd /var/www; sudo chmod 777 html

```
check with a browser that apache is working: http:\\localhost
create a phpinfo.php file in /var/www/html with content:
```
<?php phpinfo(); ?>
```
check with a browser that php is working: http:\\localhost\phpinfo.php
```
sudo usermod -d /var/lib/mysql/ mysql #needed for WSL2 environment
sudo service mysql restart
sudo mysql_secure_installation

```
Include the following line at the bottom of the file, save and quit:
```
Include /etc/phpmyadmin/apache.conf
```
Then:
```
sudo service mysql restart

sudo mysql -u root

USE mysql;
UPDATE user SET plugin='mysql_native_password' WHERE User='root';
SET PASSWORD FOR 'root'@'localhost' = PASSWORD('root');

CREATE DATABASE wordpress;
USE wordpress;
CREATE USER 'wordpress' IDENTIFIED BY 'password';
GRANT ALL ON wordpress.* TO 'wordpress';
FLUSH PRIVILEGES;

sudo curl -O https://raw.githubusercontent.com/wp-cli/builds/gh-pages/phar/wp-cli.phar; sudo chmod +x wp-cli.phar; sudo mv wp-cli.phar /usr/local/bin/wp

cd /var/www/html/
rm index.html

wp core download
wp config create --dbname=wordpress --dbuser=wordpress --dbpass="password" --dbcharset=latin1 --dbcollate=latin1_swedish_ci
wp core install --url="localhost" --title="Test Site" --admin_user=admin --admin_password="password" --admin_email=example@example.com

sudo nano provision.sh

./provision.sh -t lamp -d /var/www/html/
```





