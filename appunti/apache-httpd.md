# Apache HTTP Server

## What
- Open source project, started 1995
- Servs HTML/CSS/JS/... documents and multimedia contents


## Installation
- ubuntu based distro


## Local development
- XAMPP
- WAMP
- MAMP

## Commands
### apachectl - script to control the service ????????

sudo apachectl status
sudo apachectl start
sudo apachectl stop
sudo apachectl graceful-stop
sudo apachectl restart
sudo apachectl graceful (reload)

sudo /etc/init.d/apache 2 stop
sudo /etc/init.d/apache 2 start
sudo /etc/init.d/apache 2 graceful

## Where
### Apache files config

- ubuntu (and debian) based distro

/etc/apache2/apache2.conf

Per conferma:

apachectl -V

HTTPD_ROOT + SERVER_CONFIG_FILE

sudo find / | grep "apache2\.conf"

### Directives
- one per line
- Case-insensitive, argument case-sensitive

### .htaccess file
- immediate change without apache restart
- slower than server configuration


## VirtualHost

- based on domain name
- based on IP


## Modules

- static (core compiled included)
- shared (dynamic loading)

Debian based
- mods-enabled
a2enmod
a2dismod

## LOG

- Error log
error.log
error_log
- Access log


Loglevels
- warn (default)
- info
- emergency
- trace


/var/log/apache2


AWStats (realtime analyzer)
GoAccess (realtime access analyzer)
graylog2.org (aggregator)
logstash.net (aggregator)


## Resources
- https://www.apache.org/
- https://httpd.apache.org/
- https://httpd.apache.org/docs/current/configuring.html
- https://httpd.apache.org/docs/current/mod/directives.html
- https://httpd.apache.org/docs/current/howto/htaccess.html
- https://httpd.apache.org/docs/current/log.html
