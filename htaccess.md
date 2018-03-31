# HTTPS
```
<IfModule mod_rewrite.c>
 RewriteEngine On
 RewriteCond %{SERVER_PORT} 80
 RewriteRule ^(.*)$ https://nomedominio.ext/$1 [R,L]
 </IfModule>
```

# Browser cache
```
<IfModule mod_expires.c>
ExpiresActive On
ExpiresByType image/jpg "access 1 year"
ExpiresByType image/jpeg "access 1 year"
ExpiresByType text/css "access 1 week"
ExpiresByType text/html "access 1 month"
ExpiresByType text/x-javascript "access 1 week"
ExpiresDefault "access 1 month"
</IfModule>
```
