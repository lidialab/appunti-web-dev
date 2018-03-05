```
# HTTPS
<IfModule mod_rewrite.c>
 RewriteEngine On
 RewriteCond %{SERVER_PORT} 80
 RewriteRule ^(.*)$ https://nomedominio.ext/$1 [R,L]
 </IfModule>
