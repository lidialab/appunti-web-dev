# Connessione SSH a VM tramite coppia di chiavi
## PuTTY (Windows)
Crea la coppia di chiavi (in Windows ad esempio tramite tramite PuTTYGen)

### Chiave pubblica 
Copia la chiave pubblica nel server

Per OpenSSH vai nella tua home e crea la cartella .ssh

Crea il file authorized_keys

Modifica il file authorized_keys accodando la chiave pubblica che hai copiato da PuTTYGen su un'unica riga

```
echo "ssh-rsa AAAABBBBBBBBBBBBBBBBCCCCCCCCCCCCCC...DDDDDDDDDDDDDDEEEEEEEEEEEEEEEEEEEEE" >> .ssh/authorized_keys
```
Per Putty inserisci il nome utente per l'auto login alla voce Connection > Data > Auto-login username e imposta la chiave privata nella sessione di quella connessione alla voce Connection > SSH > Auth > Private key file for authentication

Modifica a piacere le opzioni di visualizzazione della finestra (dimensione carattere, ...)

Prova la sessione e è tutto ok salvala


Puoi copiare il file con la chiave pubblica dal terminale di Windows nella tua home del pc remoto:

```scp file.ext username@remote_ip:```

Quindi accodarla al file uthorized_keys tramite:

```cat id_rsa.pub >> .ssh/authorized_keys```