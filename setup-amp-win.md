# Installare uno stack AMP in Windows

## Apache

Il sito ufficiale https://httpd.apache.org/ per i binari per Windows rimanda a partner terzi https://httpd.apache.org/docs/current/platform/windows.html#down

Sto provando questo http://www.apachelounge.com/download/ in base a un corso che sto seguendo e poiché raccomandato col successivo download di PHP (vedi http://windows.php.net/download/ barra laterale sinistra), prerequisito è avere installato Windows® Visual Studio C++ 2017 (aka VC15/VC16/.. https://support.microsoft.com/it-it/help/2977003/the-latest-supported-visual-c-downloads) per la propria versione di Windows (installare anche la x86)

Dopo aver scaricato e scompattato lo zip sostituire nel file httpd.conf il percorso della cartella Apache da 

```c:/apache24```

a quello scelto, nel mio caso:

```c:/AMP/apache```

Cambiare

```#ServerName www.example.com:80```

in 

```ServerName localhost:80```

Avviare l'eseguibile httpd.exe e testare da browser che Apache funzioni (caricando http://localhost)

Si può impostare Apache come servizio Windows eseguendo ```httpd -k install```

Il servizio si potrà gestire sia da riga di comando

start: ```net start apache2.4``` 

stop: ```net stop apache2.4```

che da ```services.msc```

Si può rimuovere Apache come servizio Windows eseguendo ```httpd -k uninstall``` (dopo averlo stoppato)



## PHP

Il sito ufficiale http://www.php.net/ - http://it2.php.net/downloads.php per i binari per Windows rimanda a http://windows.php.net/download/

Scaricare la versione necessaria (es: la 7 Thread Safe per x64), scompattare e rinominare per brevità (nel mio caso ad esempio c:\AMP\php7), prerequisito è avere installato Windows® Visual Studio C++ 201x (aka VCxx) per la versione php scelta (installare anche la x86)

Dalla directory Php copiare ```php.ini-development``` e rinominarlo ```php.ini``` 
Essendo un ambiente di sviluppo si può attivare la visualizzazione degli errori decommentando o inserendo la riga 
```display_errors = On```

Specificare la directory di caricamento dei moduli
Esempio:
```extension_dir = "C:/AMP/php/ext"```
e attivare 

```
extension=php_mysqli.dll
extension=php_pdo_mysql.dll
extension=php_curl.dll
extension=php_gd2.dll
extension=php_gettext.dll
extension=php_openssl.dll
```


Nel file httpd.conf inserire le seguenti righe in coda al file:

```
LoadModule php7_module "C:/AMP/php7/php7apache2_4.dll"
AddHandler application/x-httpd-php .php
PHPIniDir "C:/AMP/php7"
```

PHPIniDir è la directory che contiene il file php.ini


## MySQL

Da https://www.mysql.com/downloads/ 

(Download MySQL Community Server) https://dev.mysql.com/downloads/mysql/ 

(Download MySQL Installer) https://dev.mysql.com/downloads/windows/installer/5.7.html

(mysql-installer-community-5.7.x.x.msi) https://dev.mysql.com/downloads/file/?id=474803 (include MySQL Workbench CE)

Installare anche MySQL Workbench CE, documentazione ed esempi.

Il servizio si potrà gestire sia da riga di comando

start: ```net start MySQL57``` 

stop: ```net stop MySQL57```

che da ```services.msc```

Aggiungere la directory dell'eseguibili al **PATH** di Windows (es: C:\Program Files\MySQL\MySQL Server 5.7\bin)

Editare il file ```php.ini``` abilitando:
```
extension_dir = "C:/AMP/php7/ext"
extension=php_mysqli.dll
extension=php_pdo_mysql.dll
extension=php_curl.dll
extension=php_openssl.dll
extension=php_gd2.dll
extension=php_gettext.dll
```

Curl e Openssl permettono di fare gli aggiornamenti WordPress.
GD2 serve per creare immagini (esempio: Really simple Captcha).

Al bisogno aumentare i seguenti parametri:

```
max_execution_time = 180

max_input_time = 120

memory_limit = 256M
```

## phpMyAdmin
https://www.phpmyadmin.net/

# WordPress
Per far funzionare i permalinks attivare il modulo *mod_rewrite.so* in ```httpd.conf```
```LoadModule rewrite_module modules/mod_rewrite.so``` e cambiare  “AllowOverride None” in “AllowOverride All” dove necessario.
