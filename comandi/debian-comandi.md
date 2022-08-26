# Comandi base

## Directory

### Navigare tra le directory

``` 
pwd         # print working directory
ls          # list directory
cd          # change directory
```

Riferimenti per directory speciali

```
/       # directory radice
.       # directory corrente
..      # directory superiore
~       # home directory
```

## Utenti

### Creare un nuovo utente e aggiungerlo a un gruppo

```
sudo adduser athena
sudo adduser athena sudo
sudo adduser athena www-data
```

### Crisi esistenziale (qual è il mio utente?)

```
whoami
```

### Crisi sociale (Elenco degli utenti)

```
cat /etc/passwd
```
Output:

```
[...]
athena:x:1001:1001:Athena,,,:/home/athena:/bin/bash
[...]
```
nome utente, password "nascosta", id utente (uid), id gruppo (gid), Nome completo, indirizzo, indirizzo, home directory, shell

### Cambiare password

```passwd athena```

### Switch user
``` su - minerva```

### Sudoers

Editare il file dei sudoers.

```sudo visudo```

## Gruppi

## Creare un nuovo gruppo

```
sudo addgroup athenacrew
```

## Aggiungere un utente a un gruppo

```
sudo usermod -aG athenacrew athena
```

## Togliere un utente da un gruppo

```
sudo gpasswd -d athena athenacrew
```

## Eliminare un gruppo

```
sudo groupdel athenacrew
```

### Crisi di gruppo (Elenco dei gruppi)

```cat /etc/groupfile```

## Determinare S.O. e versione
```cat /etc/issue```

```cat /etc/*-release```

# Gestione dei pacchetti
## APT - Advanced Package Tool

Le fonti da cui APT attinge i pacchetti sono elencate nel file
```/etc/apt/sources.list```

Ci sono due tipi di fonti
- **deb** per i pacchetti già compilati (i binari dei programmi)
- **deb-src** per i codici sorgenti


Ogni fonte inoltre può essere presa da un differente ramo dello stesso progetto
- **stable**
- **testing**
- **unstable**

oppure essere composta da diversi repository in base alla licenza con cui i pacchetti distribuiti
- **main** pienamente compatibile con le Debian Free Software Guidelines 
- **non-free** software che contiene alcuni elementi non-free ma che può essere distribuiito senza restrizioni
- **contrib** software open source che necessita di alcuni elementi non-free

e molti altri parametri.


*NB*

Package source : fonte del pacchetto, repository

Source package : pacchetto col codice sorgente


## Commando apt

Molti dei comandi seguenti vanno eseguiti con privilegi amministrativi, utilizzare sudo:

### Aggiornare i dati sui pacchetti disponibili
```apt update```

### Cercare software
```apt-cache search nome_pacchetto```

### Informazioni su un pacchetto di cui si conosce il nome
```apt show nome_pacchetto```

### Installare un pacchetto
```apt install nome_pacchetto```

### Re-installare un pacchetto
```apt install nome_pacchetto --reinstall```

### Rimuovere un pacchetto
```apt remove nome_pacchetto```

### Rimuovere un pacchetto compresi i file di configurazione
```apt purge nome_pacchetto```

### Aggiornamenti
```apt upgrade```

### Upgrade della versione maggiore del sistema operativo
```apt full-upgrade```

## Comando dpkg

### Cercare software
```dpkg -l | grep apache```

## Permessi file e directory
sudo chown -R www-data:www-data /var/www/html/nome_cartella/

## File system

/ root directory
| -- bin (binaries , programs)
|
| -- boot (file di boot)
|
| -- dev (device, harddisk, ...)
|
| -- etc (etsy file, configurazioni, ...)
|
| -- home (directory utenti)
|
| -- lib (librerie)
|
| -- media (drive montati automaticamente)
|
| -- mnt (drive montati manualmente)
|
| -- root (home di root)
|
| -- sbin (special binaries)
|
| -- tmp (file temporanei)
|
| -- usr
| -- -- usr/bin
| -- -- usr/sbin
|
| -- var  (logs, ...)


## Utility

### cp
Copiare file

### rm
Eliminare file

### cat
Visualizzatore del contenuto di un file

### sudo
Eseguire un comando da root

### which
Quale binario viene eseguito



