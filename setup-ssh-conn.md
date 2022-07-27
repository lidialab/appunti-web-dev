# Connessione SSH a VM tramite coppia di chiavi
## PuTTY (Windows)
Crea la coppia di chiavi tramite PuTTYGen

### Chiave pubblica 
Copia la chiave pubblica nel server

Per OpenSSH vai nella tua home e crea la cartella .ssh

Crea il file authorized_keys

Modifica il file authorized_keys accodando la chiave pubblica che hai copiato da PuTTYGen

```
echo "___ssh-rsa AAAABBBBBBBBBBBBBBBBCCCCCCCCCCCCCCCCCCCCCCDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDEEEEEEEEEEEEEEEEEEEEE___" >> .ssh/authorized_keys
```
Imposta la chiave privata nella sessione di PuTTY di quella connessione alla voce Connection > SSH > Auth > Private key file for authentication

Modifica a piacere le opzioni di visualizzazione della finestra (dimensione carattere, ...)

Salva la sessione
