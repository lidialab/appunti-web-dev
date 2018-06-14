# Installare Vagrant VVV in Windows 10 Pro

Prerequisito: virtualizzazione abilitata nel BIOS del pc

## Virtualbox

Scaricare e installare Virtualbox con privilegi amministrativi

https://www.virtualbox.org/wiki/Downloads

## Vagrant

Scaricare e installare Vagrant con privilegi amministrativi

https://www.vagrantup.com/downloads.html

### Installare il plugin Vagrant Hosts Updater (per la modifica automatica del file hosts)

Avviare GitBash con privilegi amministrativi

```vagrant plugin install vagrant-hostsupdater```

### REBOOT di Windows

### VVV

Avviare GitBash con privilegi amministrativi

```git clone -b master git://github.com/Varying-Vagrant-Vagrants/VVV.git _percorso_cartella_locale_```

duplicare ```vvv-config.yml``` in ```vvv-custom.yml```

andare nella directory _percorso_cartella_locale_

```vagrant up```

