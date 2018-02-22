# Git da linea di comando
## Bash
### Software
```
https://help.github.com/articles/set-up-git/#setting-up-git
https://git-scm.com/downloads
```
### Comandi principali
**Inizializzare un repo**

Dalla cartella che ospita il repo
```
git init
```
**Controllare lo stato di un repo**

Dalla cartella che ospita il repo
```
git status
```
**Aggiungere file ad un repo**

Dalla cartella che ospita il repo, dove ci sono nuovi file

Aggiungere TUTTI i nuovi file
```
git add .
```

Aggiungere specifici file
```
git add nomefile.ext
```

**Effettuare COMMIT in un repo**

Dalla cartella che ospita il repo
```
git commit -m "Descrizione della commit"
```

**Confrontare in un repo**

Dalla cartella che ospita il repo
```
git diff
```

**Creare un branch**

Dalla cartella che ospita il repo
```
git branch nomebrach
```

Spostarsi nel branch
```
git checkout nomebrach
```

**Creare un branch e spostarsi nel branch con un unico comando**

Dalla cartella che ospita il repo

```
git checkout -b nomebrach
```

**Elencare i branch**

Dalla cartella che ospita il repo
```
git branch
```
