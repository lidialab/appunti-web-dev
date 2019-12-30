# PHP
## Cos'è
È un linguaggio di scripting lato server

## Estensione
.php

## Preprocessor
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
```php
// commenti in linea
/* Commenti multi riga
*/
```
I commenti php non vengono inclusi nel file generato per il browser

## Output
```php
echo "Hello world";
echo 'Hello world';

echo "$var"; funziona con i doppi apici
echo "{$var}"; così è esplicito che si vuole stampare il valore della variabile
```

## Concatenazione
```php
echo "uno" . " " . "due";
$uno = "uno";
$due = "due";
$tre = $uno;
$tre .= " ";
$tre .= $due;
echo $tre;
```

## Variabili
iniziano con un $ seguito da una lettera o da un underscore (meglio evitare quest'ultimo)
sono case sensitive

```php
$nomeVariabile = 'hello';
```

### Stringhe
https://www.php.net/manual/en/ref.strings.php

### Numeri interi
```php
+= 
-=
*=
/=

++
--
```
https://www.php.net/manual/en/ref.math.php

### Numeri con decimali
https://www.php.net/manual/en/ref.math.php

### Array
#### Definizione
```php
$nomearray = array();
```

#### Definizione e assegnazione
```php
$nomeArray = array(1,2,3);
$arrayMisto = array (1,2,3, "ciao", array( "a", "b", "c") );
```

#### notazione breve da PHP 5.4 in poi
```php
$array = [1,2,3];
```

#### Assegnazione =
```php
$nomearray[5] = "sesto";
$nomearray[] = "ultimo";
```

#### Array associativi
Insieme di oggetti indicizzati per coppia di valori
```php
$arrayAssoc = array("nome" => "Lidia", "cognome" => "Pellizzaro");

echo $arrayAssoc["nome"];

$arrayAssoc["nome"] = "LidiaLAB";

$nomeArray = array(0 => 1, 1 => 2, 2 => 3);
```

#### Utilizzo
```php
echo $nomearray[0]; // -->1
echo $arrayMisto[3][0];

<pre>
echo print_r($arrayMisto);
</pre>
```

#### Funzioni per gli array
https://www.php.net/manual/en/ref.array.php

### Valori booleani
//case insensitive true TRUE false FALSE
```php
true    //-->1
false   //-->no valore
```

### NULL
//case insensitive null NULL
```php
$varNull = null;
```

### empty   *** N.B. ***
```php
  ""
  null
  0
  0.0
  "0"
  false
  array()

$varEmpty = ""; //stringa vuota
```

### casting
```php
$var = 1;
$var2 = (int) $var;
  string
  int, integer
  float
  array
  bool, boolean

gettype();
settype();
```

## COSTANTI
// senza segno del dollaro
```php
define ("NOME_COSTANTE", 3.14);
```

## Strutture di controllo
### IF
```php
if ( expression ) {
...
}
  else {
  ...
  }

if ( expression ) {
...
}
  elseif {
  ...
  }
    else {
    ...
    }
```
ATTENZIONE se una variabile viene definitiva in un statement dell'if che non viene eseguito fuori da quel if non esiste o viene creata per la prima volta, OKKIO

## Switch
```php
      switch ($var) {
        case 0:
          echo "a";
          break;
        case 1:
          echo "z";
          break;
        default:
          echo "no one";
          break;
      }
      
      switch ($var) {
        case 0:
          echo "a";
          break;
        case 1:
        case 2:
        case 3: // utilizzare lo stesso statement per più casistiche
          echo "z";
          break;
        default:
          echo "no one";
          break;
      }
```
ATTENZIONE utilizzare break altrimenti vengono eseguiti tutti i case dopo quello risultato true


## Operatori logici
### Comparazione
```php
equal: ==
!=
identical: ===
!==
<
>
<=
>=
<>
&&
||
!
```

## Operatori matematici
```php
+
-
*
/
```

### % Modulo
...


## Cicli
### While
```php
while ( expression ) {
statement;
}
```
### For
```php
for($ix = 0; $ix <= 10; $ix++) {
   echo $ix . "<br>";
}
```

### For each
```php
foreach($array as $valore) {
        echo $valore;
      }
// e per array associativi
foreach($array as $chiave => $valore) {
        echo $chiave . " " . $valore;
      }
```
### Continue
iterazione successiva
continue(n) per sapere a quale ciclo riferirsi, default è 1
### Break
interrompi
break(n) per sapere a quale ciclo riferirsi, default è 1



## Funzioni
### Definizione
```php
function nomeFunzione($nomeArgomento1, $nomeArgomento2) {
  statement;
}
```
### Utilizzo
```php
hello($nomeVariabile);
```


## Input
```php
$_SERVER
$_POST
```





