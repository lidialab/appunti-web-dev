# Personalizzare font tab attiva nel tema scuro

file *userChrome.css* nella cartella *chrome* del profilo utente, se non esiste crearla

```
.tabbrowser-tab[visuallyselected="true"] {
  color: yellow!important;
  font-weight: bold !important;
}
```

In ``about:config`` impostare il parametro ``toolkit.legacyUserProfileCustomizations.stylesheets`` a true.
