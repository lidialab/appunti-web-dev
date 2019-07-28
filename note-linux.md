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
