# PHP

[Official website](https://www.php.net/)

## Cos'è
È un linguaggio di scripting lato server (server side)

## Estensioni
L'estensione principale è .php

## Preprocessor
Il file .php viene elaborato e ne viene generato il codice HTML che sarà restituito al browser

## Tag di apertura e chiusura
```php
<?php 
...
?>
```
Quando un file php è costituito da solo codice php si può omettere il tag di chiusura alla fine del file.

È utile per prevenire linee vuote o a capo non voluti, dopo il tag di chiusura.
## Sintassi istruzioni
Vanno chiuse obbligatoriamente da ";".
Se è l'ultima istruzione prima della fine del tag di chiusura php ";" si può omettere, però meglio usarlo sempre.

## Spazi extra
php non li considera
si possono aggiungere prima e dopo il simbolo di assegnazione o le parentesi per migliorare la lettura del codice
Ma NON vanno messi quando in un echo si richiama una variabile tra parentesi graffe.

## Commenti
```php
// commento in linea
#  commento in linea
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
sono permessi lettere, cifre e underscore
sono case sensitive

```php
$nomeVariabile = 'hello';
```

### Stringhe
https://www.php.net/manual/en/ref.strings.php
apici e virgolette sono mixabili, ma vanno sempre accoppiati e soggetti ad escape quando necessario

NB: con echo è necessario utilizzare le virgolette affinché il contenuto di una variabile sia visualizzato

#### Sequenze di escape
\'
\"
\\
\n new line
\r carriage return
\t tab
\$

NB: funzionano solo con le virgolette, tranne \' che funziona anche tra apici

### Numeri interi
Operazioni con assegnazione
```php
+= 
-=
*=
/=
%=
**=

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
$nomearray[] = "ultimo"; // aggiunge l'elemento in coda
```

#### Array associativi
Insieme di oggetti indicizzati per coppia di valori
chiave + valore
chiave deve essere una stringa univoca

```php
$arrayAssoc = array("nome" => "Lidia", "cognome" => "Pellizzaro");

echo $arrayAssoc["nome"];

echo " {$arrayAssoc["nome"]} ";

$arrayAssoc["nome"] = "LidiaLAB";

$nomeArray = array(0 => 1, 1 => 2, 2 => 3);

// notazione breve
$altroArray = [
'x' => 'xxx',
'y' => 'yyy'
];
```

#### Utilizzo
La posizione degli elementi parte da 0.

```php
echo $nomearray[0]; // --> 1° elemento
echo $arrayMisto[3][0];

<pre>
echo print_r($arrayMisto);
</pre>
```
#### Array multidimensionali

```php
$altroArray = [
  [
  'regione' => 'Aosta',
  'capoluogo' => 'Aosta'
  ],
  [
  'regione' => 'Puglia',
  'capoluogo' => 'Bari'
  ],
  [
  'regione' => 'Veneto',
  'capoluogo' => 'Venezia'
  ]
];

echo $altroArray[2]['capoluogo'];
```

#### Funzioni per gli array
https://www.php.net/manual/en/ref.array.php

### Valori booleani
ESPLICITI: TRUE e FALSE
Le keywords TRUE (true) FALSE (false) sono case insensitive 
Le keywords non vanno inserite tra apici o virgolette
```php
true    //--> 1
false   //--> no valore
```

IMPLICITI
FALSE impliciti:
0, 0.0, "0", '', ""
array vuoto
NULL
variabili solamente dichiarate, ma non valorizzate

### NULL
case insensitive null NULL
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
// senza segno del dollaro, per convenzione si scrivono in maiuscolo
```php
define ("NOME_COSTANTE", 3.14);
define ('PI_GRECO', 3.14);
```

## Operatori
### Operatori logici
```php
&&
||
!
```
### Operatori di comparazione
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
```
C'è anche questo, ma non l'ho esaminato...
```
$a <=> $b 	Spaceship 	Un int minore di, uguale a, o maggiore di zero quando $a è minore di, uguale a, o maggiore di $b. 
```

### Operatori aritmetici
```php
+
-
*
/
%    Modulo
**   Esponenziale (da PHP 5.6)
```
NB: -$var --> negativo

### Precedenze degli operatori
...

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

#### Sintassi IF breve
if ( xxx ) : yyy ;
if ( xxx ) : yyy elseif ( zzz ) else : www endif;

#### Operatore ternario
$res = condizione ? vero : falso;
$res = $var ?: falso; //versione breve in cui se è vero il valore di $var è assegnato a $res
$res = $var ?? falso; //PHP 7 ; versione breve in cui se è vero il valore di $var è assegnato a $res, se $var non è definito viene calcolata l'espressione per false.

### Switch
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
      
            
      switch ($var) {
        case $var < 0:
          echo "a";
          break;
        case $var > 0:
          echo "z";
          break;
        case $var == 0:
          echo "az";
      }
```
I valori di comparazione possono essere boolean, number, string. Per una comparazione diversa da "è uguale a" si deve costruire l'intera espressione che così sarà valutata se vera o falsa (boolean).
ATTENZIONE utilizzare break altrimenti vengono eseguiti tutti i case dopo quello risultato true

## Cicli
### While
```php
while ( expression ) {
statement;
}
```
### Do While
```php
do {
statement;
} while ( expression );
```
### For
```php
for ( $ix = 0; $ix <= 10; $ix++ ) {
   echo $ix . "<br>";
}
```

### For each
```php
foreach ($array as $valore) {
        echo $valore;
      }
// e per array associativi
foreach ($array as $chiave => $valore) {
        echo $chiave . " " . $valore;
      }
```

### Continue
iterazione successiva
continue(n) per sapere a quale ciclo riferirsi, default è 1
### Break
interrompi
break(n) per sapere a quale ciclo riferirsi, default è 1

### Sintassi alternative
while (condizione) : 
  echo "fai qualcosa";
endwhile;

for (condizione) :
  echo "fai qualcosa";
endfor;

foreach (condizione) :
  echo "fai qualcosa";
endforeach;

## Funzioni
### Definizione
```php
function nomeFunzione($nomeArgomento1, $nomeArgomento2=valoreDefault) {
  statement;
}
```
È buona pratica far precedere al nome di funzione un acronimo che ne renda il nome univoco.
Es: ll_nomefunzione

### Utilizzo
```php
nomeFunzione($nomeArgomento1, $nomeArgomento2);
nomeFunzione($nomeArgomento1); // se c'è un valore di default l'argomento può essere saltato
nomeFunzione(&$nomeArgomento1); // viene passato il riferimento alla memoria della variabile vera e propria che verrà modificata se citata all'interno della funzione
```
### callback
... es: usort()

### Ritornare un valore da una funzione
```php
return($ris);
```
Return termina l'esecuzione della funzione

### Scope di una variabile
Locale, all'interno di una funzione
Globale


## Input

```php
$_SERVER
$_GET
$_POST
```
Le variabili ```$_GET``` e ```$_POST``` sono entrambe create e presenti, ma solo un form le può valorizzare.
Utilizzare GET solo per i form di ricerca, così possono essere memorizzati nei preferiti includendo la stringa cercata.
html_entities converte "tutto" tranne apici singoli.

## Output

### echo
echo può visualizzare una serie di dati separati da ","
c'è una versione abbreviata ```<?=  ?>``` ma la relativa opzione deve essere attiva nel server
Se sono presenti nomi di variabili e sono usati gli apici singoli vengono stampati i nomi delle variabili.
Se sono presenti nomi di variabili e sono usati gli apici doppi vengono stampati i valori delle variabili.
Se vengono usati gli apici doppi il nome della variabile dopo il simbolo del dollaro può essere racchiuso tra parentesi graffe per evidenziare la presenza di una variabile. ES: echo "Ciao ${NOME}";

### print
print può visualizzare un solo argomento 

### print_r
print può visualizzare un solo argomento oppure un array

### var_dump
stampa il tipo di variabile, la lunghezza e il suo contenuto

### var_export()
stampa la variabile come una stringa con gli apici

## Oggetti
...

## Includere un file
include //se il file manca segnala un warning, ma continua
include_once //viene incluso una sola volta anche se menzionato più volte nello script

require //se il file manca va in errore
require_once //viene incluso una sola volta anche se menzionato più volte nello script

Possono essere utilizzate diverse estensioni, ma meglio utilzzare .php (se proprio si vuole utilizzare "inc" optare per .inc.php).
NB: la definizione di una funzione contenuta in un file esterno DEVE essere inclusa PRIMA dell'utilizzo della funzione. A differenza di un unico file php in cui la funzione è sia definita che utilizzata e l'ordine non ha importanza.

Non servono le parentesi. Meglio utilizzare un path relativo.

Per riferirsi ad altri file in un file che viene incluso utilizzare una variabile che definisce il percorso principale e viene definita nel file che lo richiama.

Può essere utile fare debugging con get_include_path()
Può essere utile definire il percorso degli inlcude con set_include_path, in tal caso è raccomandato utilizzare come separatore di cartelle la variale PATH_SEPARATOR.

### Date
```
date()
```

## Troubleshooting
- errori di sintassi
- visualizzare le variabili di cui si sospetta un valore inaspettato (echo/print_r/gettype/var_dump/get_defined_vars/debug_backtrace)
- provare ad eseguire ```phpinfo();```
- verificare i path
- utilizzare il display degli errori
- controllare i log
- utilizzare tool come Xdebug
- se un file che viene incluso contiene righe vuote dopo aver chiuso il tag php l'header del file HTML viene generato e può causare problemi di HEADERS già inviati.
- se il problema riguarda degli include/require controllare anche i permessi dei file o se i file siano corrotti, in ques'ultimo caso rieffettuare l'upload dei file


# php.ini
Con phpinfo(); si può vedere qual è la posizione del file php.ini caricato "loaded configuration file"
Quando di apporta una modifica si deve riavviare il server web
date.timezone
display_errors
error_reporting

## .htaccess
Alcune modifiche possono essere apportare tramite il file .htaccess nei server web apache, se consentito dall'hosting
php_value direttiva valore
php_flag direttiva on
php_flag direttiva off

## user.ini
Alcune modifiche possono essere apportare tramite il file user.ini, se consentito dall'hosting
Lo si compila come il php.ini

## runtime_config.php
Alcune modifiche possono essere apportare tramite l'esecuzione di uno script php, se consentito dall'hosting
Si utilizzano apposite funzioni come ini_set('display_errors', '1'); .

# Approfondimenti
Sintassi heredoc, utile nella costruzione di query per DB

## Date e orario
### 32bit vs 64bit
Si basa su timestamp e calcola le date da una data fissata come differenza di secondi. La data dipende dal sistema, se è a 32bit o 64bit.
x86: 1970-01-01 (1901-12-31 --> 2038-01-19)
x64: (sistema x64 con binari php x64) -290 miliardi di anni e +290 miliardi di anni
Se si utilizzano gli oggetti invece viene sempre supportato il range completo e gli UTC indipendenti dal sistema su cui sono eseguiti.

PHP 4: il range supportato dalle funzioni date(), getdate(), strtotime() dipende se girano sun php compilato a 32 o 64 bit, utilizzano il fuso orario del sistema in cui girano
PHP 5.2: la classe DateTime supporta sempre il range esteso e l'utilizzo di fusi orari indipendenti dal sistema in cui gira, anche se a 32bit
