# Comandi base

## Help
```help```
```info```
```man```
```apropos```

```comando -h```
```comando --h```
```comando --help```


## ps
quali processi sono in esecuzione? (tra cui la shell)


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

```
id
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

### Chi è collegato
```who```

## Gruppi

### Creare un nuovo gruppo

```
sudo addgroup athenacrew
```

### Aggiungere un utente a un gruppo

```
sudo usermod -aG athenacrew athena
```

### Togliere un utente da un gruppo

```
sudo gpasswd -d athena athenacrew
```

### Eliminare un gruppo

```
sudo groupdel athenacrew
```

### Crisi di gruppo (Elenco dei gruppi)

```cat /etc/groupfile```

## Determinare S.O. e versione
```cat /etc/issue```

```cat /etc/*-release```

## Determinare hostname
```hostname```

## Determinare cose
```uname```
```ip```
```ss```
```netstat```
```env```

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



## shell
shell in uso:
```
echo $0
```

percorso della shell in uso:
```
echo $SHELL
```

modificare la shell in uso al login dal file /etc/passwd:
```
nomeutente:x:1001:1001::/home/nomeutente:/bin/nomeshell
```

## Gestione pacchetti Debian

## dpkg

## apt ~ apt-get

Con Debian Jessie è stato introdotto apt che unisce funzionalità di apt-get e apt-cache e ha migliorato l'output a favore dell'utente. Per casi complessi sarà preferibile utilizzare apt-get. 

```
apt search stringa
sudo apt install nome_pacchetto
sudo apt remove nome_pacchetto
sudo apt update
sudo apt upgrade

apt full-upgrade
apt autoremove
apt list -a nome_pacchetto
apt show nome_pacchetto
apt show -a nome_pacchetto
```

## Accesso remoto
```
sudo apt install ssh
```
È poi consigliato creare una coppia di chiavi crittografata per accedere in alternativa alla coppia user-password

## Fonti
[Debian reference](https://www.debian.org/doc/manuals/debian-reference/)
[The Debian Administrator's Handbook - Debian Jessie (8) from Discovery to Mastery](https://www.debian.org/doc/manuals/debian-handbook/index.en.html)
[D.3.7. Accesso remoto: installazione di SSH e impostazione dell'accesso](https://www.debian.org/releases/stable/amd64/apds03.it.html#idm4535)


## Info utili
[Spazio su disco necessario per i task - amd64](https://www.debian.org/releases/stable/amd64/apds02.it.html)
[Release Debian] (https://www.debian.org/releases/)



## Servizi (daemon) / Services (daemons)

```ps``` --> programmi lanciati dall'utente
```ps aux``` --> daemons
```pstree```

Systemd --> Master daemon (id 1)
init system

Boot --> Kernel --> systemd --> fs, services, ...


```systemctl``` --> send control commands to the system manager
unit --> daemon

```systemctl opzioni comando  nome_servizio```

comandi:

```
status
start
stop
restart
reload
reload-or-restart
enable
disable
is-enable
```

## Processi / Processes
Processo: istanza di un programma in esecuzione

Foreground processes
Background processes



### ps
```ps``` 					--> ciò che è in esecuzione nel terminale
```ps -u nomeutente```		--> processi utente
```ps aux```

### top
```top```
```htop```

### kill
pid --> process id
send kill signal, default is 15
```kill -l```
CTRL C --> 2
CTRL Z --> 19
CTRL Z --> 18 (Control Z seconda volta)
```kill pid```
```pgrep nome_processo``` --> restituisce l'id del processo



### jobs

### bg /fg

## LOG

```journalctl -xe```

