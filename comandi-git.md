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

Aggiungere e spiegare:
```
git log
git remote add origin https://github.com/nome-utente/nome-repo.git
git push -u origin master
```

## Riferimenti
- http://rogerdudler.github.io/git-guide/index.it.html
- https://services.github.com/on-demand/downloads/it/github-git-cheat-sheet/