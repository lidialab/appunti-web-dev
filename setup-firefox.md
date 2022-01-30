# Personalizzare font tab attiva nel tema scuro

file *userChrome.css* nella cartella *chrome* del profilo utente, se non esiste crearla

```
.tabbrowser-tab[visuallyselected="true"]:-moz-lwtheme {
  color: yellow!important;
  font-weight: bold !important;
}
```
