# Git da linea di comando
## Software
```
https://help.github.com/articles/set-up-git/#setting-up-git
https://git-scm.com/downloads
```
## Bash
### Comandi principali
**Configurazione globale**

Imposta nome ed email da mostrare nelle commit effettuate
```
git config --global user.name "[name]"
git config --global user.email "[email]"
```

**Inizializzare un repo**

Dalla cartella che ospita il repo
```
git init
oppure
git init [project-name]
```
**Controllare lo stato di un repo**

Dalla cartella che ospita il repo, elenca i file nuovi o modificati
```
git status
```
**Aggiungere modifiche ad un repo (staging)**

Dalla cartella che ospita il repo, dove ci sono nuovi file

Aggiungere TUTTI i nuovi file e aggiornare quelli modificati
```
git add .
```

Aggiungere specifici file
```
git add nomefile.ext
```

Aggiornare i file modificati e togliere quelli cancellati
```
git add -u
```

Caricare TUTTE le modifiche (anche cancellare file)
```
git add -A
```

**Effettuare COMMIT in un repo**

Dalla cartella che ospita il repo
```
git commit -m "Descrizione della commit"
```

**Confrontare in un repo**

Dalla cartella che ospita il repo mostra le differenze non ancora staged
```
git diff
```

Mostra le differenze dall'ultima modifica staged
```
git diff --staged
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

**Merge di branch**

Dalla cartella che ospita il repo, con attivo il branch che RICEVE (di solito il master)
*RACCOMANDAZIONE*: i due branch devono essere puliti (git status --> pulito)
```
git merge nomebranch
```

**Visualizzare quali merge di branch sono stati fatti**

Dalla cartella che ospita il repo master
```
git brach --merged
git brach --nomerge
```

**Cancellare un branch**

Dalla cartella che ospita il repo master

```
git branch -d nomebrach
```

**Clona un progetto esistente online e il suo storico git**

```
$ git clone [url]
```

**Push file to repo**

```
git remote add origin https://github.com/nome-utente/nome-repo.git
git push -u origin master
$ fornire utente e password
```

**Pull file from repo** - DA DEFINIRE MEGLIO
```
git pull
```

**xxx**
```
```

**xxx**
```
```
**xxx**
```
```

### .gitignore file
Escludi file e percorsi 
```
*.log
build/
temp-*
```

## Riferimenti
- http://rogerdudler.github.io/git-guide/index.it.html
- https://services.github.com/on-demand/downloads/it/github-git-cheat-sheet/
