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

## Output
echo "Hello world";
echo 'Hello world';

echo "$var"; funziona con i doppi apici
echo "{$var}"; così è esplicito che si vuole stampare il valore della variabile

## Concatenazione
echo "uno" . " " . "due";
$uno = "uno";
$due = "due";
$tre = $uno;
$tre .= " ";
$tre .= $due;
echo $tre;

## Variabili
iniziano con un $ seguito da una lettera o da un underscore (meglio evitare quest'ultimo)
sono case sensitive

```php
$nomeVariabile = 'hello';
```

## Stringhe
https://www.php.net/manual/en/ref.strings.php

## Numeri interi
+= 
-=
*=
/=

++
--


## Numeri con decimali


## Array
### Definizione
$nomearray = array();
### Definizione e assegnazione
$nomeArray = array(1,2,3);
### Utilizzo
echo $nomearray[0]; // -->1


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





