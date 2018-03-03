Prima bozza

```html
<html>
<head>
<title>Programmazione JavaScript</title>
</head>

<!-- type="text/javascript" non è più necessario -->

<script type="text/javascript">
// commenti in JavaScript su una sola riga
/* 
   commenti in JavaScript 
   su più righe 
*/

//variabili, dichiarazione
var x = 3.16;
var y = 'a';
var z = 'bc';

// concatenazione --> +
// document.write(y+z);

/* 
data types

numbers
strings
boolean
null
undefined

*/

/* 
funzioni
*/
function nomeFunzione (arg1, arg2) {

document.write(arg1 + " è una " + arg2);

}

/* 
scope delle variabili

globali: variabili dichiarate fuori dalle funzioni
locali: variabili dichiarate nelle funzioni

*/


/* 
  Operatori aritmetici
  + - / * 
  
  Operatori di assegnamento
  =
  += -=
  =+ =-
  
  Operatori di comparazione
  < > <= >= == !=
  === strict equal to
  !== not strict equal to
  
  Operatori logici
  &&
  ||
  !
  esempio per not:
  !()
  
*/

/* 
  Condizioni
  if () {} else {}
   
  if () {} else if {} else {}
  
*/


/* 
  Switch
  
  switch (nomeVariabile){
  
	case "valore-con-cui-comparare":
		istruzioni;
		break;
	case "valore-con-cui-comparare":
		istruzioni;  
		break;
	default:
		istruzioni; 
  }

*/

/* 
  
  
  

*/



</script>
<!-- script richiamati da file esterno -->
<script type="text/javascript" src=".js"></script>

<body>

<script>
document.write("<h1>hello world</h1>"); // output nel documento
window.alert("Questo è un alert !!!");  // popup
document.write("<h2>hello world 2</h2>"); // output nel documento
nomeFunzione ('nomeFunzione','funzione');
window.prompt("Inserisci il tuo nome");  // input (Prompt)
</script>

</body>

</html>
```

Fonti:
Programmare con JavaScript dalle basi ad Ajax di Ivan Venuti - Edizioni FAG Milano - 2010
varie:
OnClick Academy JavaScript Fundamentals
https://onclick-academy.teachable.com/courses/enrolled/121182
