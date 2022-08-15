# Comandi base
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
