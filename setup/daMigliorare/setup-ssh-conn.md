# Connessione SSH a VM tramite coppia di chiavi
## PuTTY (Windows)
Crea la coppia di chiavi tramite PuTTYGen

### Chiave pubblica 
Copia la chiave pubblica nel server

Per OpenSSH vai nella tua home e crea la cartella .ssh

Crea il file authorized_keys

Modifica il file authorized_keys accodando la chiave pubblica che hai copiato da PuTTYGen su un'unica riga

```
echo "___ssh-rsa AAAABBBBBBBBBBBBBBBBCCCCCCCCCCCCCC...DDDDDDDDDDDDDDEEEEEEEEEEEEEEEEEEEEE___" >> .ssh/authorized_keys
```
Imposta la chiave privata nella sessione di PuTTY di quella connessione alla voce Connection > SSH > Auth > Private key file for authentication

Modifica a piacere le opzioni di visualizzazione della finestra (dimensione carattere, ...)

Salva la sessione
