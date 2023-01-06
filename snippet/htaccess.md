# HTTPS
```
<IfModule mod_rewrite.c>
 RewriteEngine On
 RewriteCond %{SERVER_PORT} 80
 RewriteRule ^(.*)$ https://nomedominio.ext/$1 [R,L]
</IfModule>
```
# 000-default.conf

sudo nano /etc/apache2/sites-available/000-default.conf

```
<VirtualHost *:80>
   ServerAdmin example@example

   RewriteEngine On
   RewriteCond %{HTTPS} off
   RewriteRule ^(.*)$ https://%{HTTP_HOST}$1 [R=301,L]
</VirtualHost>
```

# Browser cache
```
<IfModule mod_mime.c>
AddType image/x-icon cur ico
</IfModule>
#
<IfModule mod_expires.c>
# attivazione
ExpiresActive On
# default
ExpiresDefault "access plus 1 month"
# immagini
ExpiresByType image/jpg                          "access 1 month"
ExpiresByType image/jpeg                         "access 1 month"
ExpiresByType image/gif                          "access 1 month"
ExpiresByType image/png                          "access 1 month"
ExpiresByType image/webp                         "access 1 month"
ExpiresByType image/svg+xml                      "access 1 month"
ExpiresByType audio/ogg                          "access 1 month"
ExpiresByType video/mp4                          "access 1 month"
ExpiresByType video/ogg                          "access 1 month"
ExpiresByType video/webm                         "access 1 month"
# codice                                         
ExpiresByType text/html                          "access 1 week"
ExpiresByType text/css                           "access 1 week"
ExpiresByType application/javascript             "access 1 week"
ExpiresByType application/xhtml+xml              "access 1 week"
ExpiresByType application/x-javascript           "access 1 week"
ExpiresByType text/javascript                    "access 1 week"
ExpiresByType application/json                   "access 0 seconds"
ExpiresByType application/ld+json                "access 0 seconds"
ExpiresByType application/schema+json            "access 0 seconds"
ExpiresByType application/vnd.geo+json           "access 0 seconds"
ExpiresByType application/xml                    "access 1 week"
ExpiresByType text/xml                           "access 1 week"
# pdf                                            
ExpiresByType application/pdf                    "access 1 month"
# font
ExpiresByType application/vnd.ms-fontobject      "access 1 month"
ExpiresByType font/woff                          "access 1 month"
ExpiresByType font/woff2                         "access 1 month"
ExpiresByType application/font-woff              "access 1 month"
ExpiresByType application/x-font-woff            "access 1 month"
ExpiresByType application/font-woff2             "access 1 month"
ExpiresByType application/x-font-opentype        "access 1 month"
ExpiresByType font/ttf                           "access 1 month"
ExpiresByType font/otf                           "access 1 month"
ExpiresByType font/collection                    "access 1 month"
ExpiresByType font/sfnt                          "access 1 month"
ExpiresByType application/vnd.ms-fontobject      "access 1 month"
ExpiresByType font/eot                           "access 1 month"
ExpiresByType font/opentype                      "access 1 month"
ExpiresByType application/x-font-ttf             "access 1 month"
# icona
ExpiresByType image/x-icon                       "access 1 month"
ExpiresByType image/vnd.microsoft.icon           "access 1 month"
# Web feeds 
ExpiresByType application/atom+xml               "access 15 minutes" 
ExpiresByType application/rss+xml                "access 15 minutes"
ExpiresByType application/rdf+xml                "access 15 minutes"
</IfModule>
```

# Compressione 
```
<IfModule mod_deflate.c>
AddOutputFilterByType DEFLATE text/css text/html text/plain application/javascript text/x-component text/xml application/json application/atom+xml application/rss+xml application/xhtml+xml application/xml application/vnd.ms-fontobject application/x-font-ttf font/opentype image/svg+xml image/x-icon
</IfModule>
```
