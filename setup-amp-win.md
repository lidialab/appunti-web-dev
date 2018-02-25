# Installare uno stack AMP in Windows

## Apache

Il sito ufficiale https://httpd.apache.org/ per i binari per Windows rimanda a partner terzi https://httpd.apache.org/docs/current/platform/windows.html#down

Sto provando questo http://www.apachelounge.com/download/ in base a un corso che sto seguendo, prerequisito è avere installato Windows® Visual Studio C++ 2017 (aka VC15) per la propria versione di Windows

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

stop: ```net start apache2.4```

o da ```services.msc```

Si può rimuovere Apache come servizio Windows eseguendo ```httpd -k uninstall``` (dopo averlo stoppato)



