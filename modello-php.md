# PHP
## Cos'è
È un linguaggio di scripting lato server

# Estensione
.php

# Preprocessor
Il file .php viene elaborato e genera il file HTML che sarà restituito al browser

## Tag di apertura e chiusura
```php
<?php 
...
?>
```
Quando un file php è costituito da solo codice php si può omettere il tag di chiusura alla fine del file.

È utile per prevenire linee vuote o a capo non voluti, dopo il tag di chiusura.

## Commenti
// commenti in linea
/* Commenti multi riga
*/
I commenti php non vengono inclusi nel file generato per il browser

## Variabili
Case sensitive
```php
$nomeVariabile = 'hello';
```

## Funzioni
```php
function hello($nomeVariabile) {
  echo $nomeVariabile;
}

hello($nomeVariabile);
```

## Strutture di controllo
```php
if() {
...
}
  else {
  ...
  }

if() {
...
}
  else if {
  ...
  }
    else {
    ...
    }
```

## Input
```php
$_SERVER
$_POST
```





