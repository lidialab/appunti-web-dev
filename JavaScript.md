Appunti JS

```html
<!DOCTYPE html>
<html lang="it">

<head>
    <meta charset="utf-8">    <!-- lasciare entro i primi 1024 byte -->
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <title>JavaScript Skeleton</title>
    <!-- 
        JavaScript è case SENSItive
            è comune utilizzare la scrittura camelCase per i nomi di:
                COSTANTI tutto in MAIUSCOLO
                variabiliInizianoConMinuscola
                Oggetti e Classi iniziano con la Maiuscola
    -->
    
    <script type="text/javascript">
        // commenti in JavaScript su una sola riga
        /* 
           commenti in JavaScript 
           su più righe 
        */        
    </script>

    <!-- script richiamati da file esterno nel head -->        
    <script type="text/javascript" src="fileEsterno.js"></script>
    <!-- type="text/javascript" non è più necessario ??? -->

    <!-- 
        File JavaScript Esterno nell'head
        ATTENZIONE all'effetto JavaScript Rendering Blocking
        HTTP/2 attenua questo problema
    -->
    <script type="text/javascript" src="fileEsterno1.js">//JavaScript Loading Immediato</script>
    <script type="text/javascript" src="fileEsterno2.js" async>//JavaScript Loading Asincrono</script>
    <script type="text/javascript" src="fileEsterno3.js" defer>//JavaScript Loading Differito</script>

    <script type="text/javascript">
    // inline javascript nell'head, viene eseguito prima del caricamento della pagina
        nomeFunzione();           
    </script>

    <script type="text/javascript">
    // dichiarazione variabili
        var x = 3.16;
        var y = 'a';
        var z = 'bc';
        var nomeVariabile;
        var a, b, c;
    // assegnazione variabili ; se non è stata dichiarata prima JavaScript la crea (!!!...)
        nomeVariabile = 'qualcosa';
    // dichiarazione e assegnazione in unica riga
        var nomeVariabile2 = 'qualcosa';

    // ATTENZIONE: se una variabile non viene dichiarata la prima volta che viene usata JS assume che è una nuova variabile e se la dichiara da solo...

    // data type
    
    // numeri
    var intero = 1;
    var decimale = 1.678;
    // stringhe
    // carattere di escape -->  \
    var stringa1 = "stringa";
    var stringa2 = 'stringa';
    // boolean
    var vero = true;
    var falso = false;
    // null
    var variabileNull = null;
    // undefined
    var variabileUndefined;
    // symbol
    
    // typeof per sapere di che tipo è la variabile
    console.log(typeof vero); //--> boolean
    console.log(typeof variabileNull); //--> object


    // Array --> Oggetti
    /*
        Dichiarazione
        nomeArray = new Array("a","b","c");
        Dichiarazione breve
        nomeArray2 = ["a","b","c"];

        var copiaSecondoValoreDellArray = nomeArray[1];

        Proprietà 
        var nElementiArray = nomeArray2.lenght;

        Metodi --> nomeArray.metodo()
        reverse
        shift
        unshift
        pop
        push
        splice
        slice
        indexOf
        join

    */

    // Operatori
    /*

    Operatore di assegnamento
    =

    Operatori aritmetici
    + - / * ()
    
    Operatori di assegnamento aritmetici
    =
    += -=
    =+ =-
    *= 
    /=
    
    Operatori unari
    ++
    --
    ++a    --> eseguito immediatamente
    a++    --> eseguito dopo la valutazione
    
    Operatori di comparazione
    == != < > <= >=
    === strict equal to         --> anche il tipo corrisponde
    !== not strict equal to     
    
    Operatori logici
    &&
    ||
    !
    nb, not con parentesi:
    !()

    XOR (vero il primo o vero il secondo, ma non entrambi) --> if ( ( a == b ) || ( c == d ) ) && ( ( a == b ) != ( c == d ) ) {}


    Operatore di concatenamento / concatenazione 
    +
    var a = 1;
    var b = "2";
    var somma = a + b; --> 12
    document.write(y+z);

    - * / darebbero come risultato NaN : not a number

    
    Operatore ternario
    a == b ? fai-qualcosa : altrimenti-fai-qualcosaltro;


  Condizioni
      if () {} else {}
       
      if () {} else if {} else {}
  

  Switch
  
      switch ( nomeVariabile ){
      
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

    // Cicli
    /*
        FOR
        for ( var ix = 0 ; i < 10; ix++ ) { istruzioni }
        
        WHILE
        var ix = 0;
        while ( ix < 10 ) { istruzioni; ix++; }

        DO WHILE
        var ix = 0;
        do { istruzioni; ix++; } while ( ix < 10 );

        ARRAY e Cicli

        for ( var ix = 0 ; ix < nomeArray.lenght; ix++ ) { istruzioni }        
        
        Esempio utile:
        extLinks = document.querySelectorAll('a[href^="http://nome.dominio"');
        for ( var ix = 0 ; ix < extLinks.lenght; ix++ ) { 
            if ( !extLinks[ix].hasAttribute("target") ) {
                extLinks[ix].setAttribute("target","_blank");
            }
         }

         BREAK
         per terminare il ciclo

         CONTINUE
         per terminare l'iterazione corrente e continuare col ciclo

    */

    // Funzioni
    /*
        Non importa quando è dichiarata perché il browser carica tutto il file js prima di eseguirlo
        Importa invece l'ordine in cui sono dichiarate le variabili e richiamata la funzione

        function nomeFunzione(param1, param2) {
    
        }

        Named
        function nomeFunzione(param1, param2) {
            istruzioni;
            param3 = param1 + param2;
            return param3;
        }
        
        Richiamare la funzione:
        var param1 = "a";
        var param2 = "b";
        var param3 = "c";
        var param4;
        param4 = nomeFunzione(param1, param2);
        --> param4 è un oggetto

        Anonymous
        var nomeVariabile = function() {
            istruzioni;
            return valore;
        }

        console.log(nomeVariabile());


        Immediately invoked
        var a = "a";
        var b = "b";
        var nomeVariabile = (function(a,b) {
            istruzioni;
            return valore;
        })(1,2)

        console.log(nomeVariabile());

   
    */

    //  scope delle variabili
    /* 
        globali:    variabili dichiarate fuori dalle funzioni
                    variabili NON dichiarate (col  var), anche se all'interno di una funzione
        locali:     variabili dichiarate nelle funzioni
                    le variabili locali sono cancellate all'uscita della funzione e quindi liberano risorse


        ES2015 let e const
            const
            costanti
            const NOMECOSTANTE = valore;


            let
            variabile con scope limitato a un blocco
            function nomeFunzione() {
                var variabileLocale = 3.14;
                istruzioni;

                if (condizione) {
                    let variabileLocale = 6.325;
                    console.log(variabileLocale); --> 6.325
                }

                console.log(variabileLocale); --> 3.14
            }


    */

    // Oggetti
    /*
        var nomeOggetto = new Object();
        nomeOggetto.nomeproprietà1 = "a";
        nomeOggetto.nomeproprietà2 = "b";
        nomeOggetto.nomeproprietà3 = "c";

        var nomeOggetto = {
            nomeproprietà1 : "a",
            nomeproprietà2 : "b",
            nomeproprietà3 : "c",
            nomeFunzione : function() { istruzioni }
        }

        Costruttori
        function NomeCostruttore(a,b,c) {
            this.a = a;
            this.b = b;
            this.c = c;
            this.nomeFunzione = function() { istruzioni };
        }


        var nuovoCorso = new NomeCostruttore("a","b","c");

        var iNostriCorsi = [
            new NomeCostruttore("a","b","c"),
            new NomeCostruttore("aa","bb","cc")
        ];

        DOT notation
        nomeOggetto.nomeProprietà

        BRACKET notation --> quando la proprietà deve essere convertita è l'unica notation che funziona
        nomeOggetto["nomeProprietà"]


    */

    // DOM - Document Object Model, descrive le relazioni tra elementi html, è l'API per CSS e JS per modificare html
    /*
        il browser --> BOM Browser Object Model
        windows
         document --> DOM
            head
                meta
                title
                link
            body
                header
                    a
                main
                    ul
                        li
                        li
                        li
                footer
                    ...


        Nodi - Node Tree

        Come puntare

        document.body
        document.getElementById("nome-id")
        document.getElementsByClassName("nome-classe-css")
        document.getElementsByTagName("nome-tag-html")
        document.querySelector("selettore-css")         --> solo la prima volta che lo si incontra
        document.querySelectorAll("selettore-css")      --> tutti

        Come cambiare il nodo

        document.querySelector("selettore-css").innerHTML = "Nuovo testo";

        Come ottenere le classi

        document.querySelector("selettore-css").classList  --> read only 

        Come cambiare le classi

        add
        document.querySelector("selettore-css").add("nuovaClasse");
        remove
        document.querySelector("nuovaClasse").remove("nuovaClasse");
        toggle
        document.querySelector("nuovaClasse").classList.toggle("selettore-css"); --> se ritorna true è stata aggiunta, se ritorna false è stata rimossa
        contains
        document.querySelector("nuovaClasse").classList.contains("selettore-css"); --> se ritorna true c'è, se ritorna false non c'è 

        Come cambiare gli attributi

        nomeElemento.hasAttribute()
        nomeElemento.getAttribute()
        nomeElemento.setAttribute()
        nomeElemento.removeAttribute()

        esempio:

        const ELEMENTO = document.querySelector("selettore-css"); --> la costante impedisce cambi accidentali
        
        if ( ELEMENTO.hasAttribute("target") ) {
            console.log( ELEMENTO.getAttribute("target") );
            }
            else
            {
            ELEMENTO.setAttribute("target", "_blank");
            }

        
        Come aggiungere nodi, cross-browser
        
        esempio: aggiungere figcaption

        const TARGETIMG = document.querySelector("selettore-css");
        const THEIMAGE = TARGETIMG.querySelector("img");

        var altText = THEIMAGE.getAttribute("alt");

        var captionElement = document.createElement("figcaption");

        var captionText = document.createTextNode(altText);

        captionElement.appendChild(captionText);

        TARGETIMG.appendChild(captionElement);

        THEIMAGE.setAttribute("alt","");

        Come aggiungere CSS inline
        document.querySelector("selettore-css").style
        document.querySelector("selettore-css").style.color = "black";
        document.querySelector("selettore-css").style.backgrundColor = "white"; --> nomi con trattino diventano camelCase
        tutti questi rimpiazzano o aggiungono il singolo stile

        document.querySelector("selettore-css").style.cssText = "margin: 1em; color: yellow;" --> rimpiazza tutto lo style

        document.querySelector("selettore-css").setAttribute("style","margin: 1em; color: yellow;"); --> rimpiazza tutto lo style

        ATTENZIONE: meglio creare regole CSS e applicarle o rimuoverle attraverso il JS per mantenere la separazione tra presentazione e interattività

    */

    // DOM - Eventi
    /*
        Event handling

        browser event
            load
            error
            online/offline
            resize
            scroll
        document event
            focus
            blur
            reset/submit
            mouse event click/mouseover/...
        Media events
        Progress Event
        CSS transition

        Event reference --> MDN

        Esempio:

        <div class="cta">
            <a href="#">Book now</a>
            <section id="booking-alert">info info info</section>
        </div>

        const CTA = document.querySelector(".cta a");
        const ALERT = document.querySelector("#booking-alert");

        CTA.classList.remove("hide");
        ALERT.classList.add("hide");

        function reveal(e) {
            e.preventDefault();
            CTA.classList.toggle("hide");
            ALERT.classList.toggle("hide");    
        }

        CTA.onclick = reveal; // senza parentesi: eseguita solo al clic
        
        oppure 
        Event listener  --> permette più azioni
        
        CTA.addEventListener("click", reveal, false);
        CTA.addEventListener("click", function(){console.log("clicked!");}, false);

        passare parametri alle funzioni negli event listener
        function reveal(e,current) {
            e.preventDefault();
            current.innerHTML = "New value";    
            ALERT.classList.toggle("hide");  
        }

        CTA.addEventListener("click", function(e){ reveal(this); }, false);
        
        

    */



    </script>
</head>

<body>

        <script type="text/javascript">
        // inline javascript nel body, viene eseguito 
            nomeFunzione();           
        </script>

        <!-- script richiamati da file esterno nel body -->
        <script type="text/javascript" src="fileEsterno4.js"></script>

    </main>

        <h2>Validation Tools</h2>
        ESLINT --> ATOM (https://www.lynda.com/JavaScript-tutorials/Automate-script-linting/574716/612098-4.html); eslint.org ; npmjslint xo<br> 
        Syntax High light <br>
        Online linting tools: jslint.com --> strict validation;  jshint.com ;

        <h2>Debug Tools</h2>
        Developer Tools - aprire la console!<br>
        Developer Tools - Step by Step, Breakpoints (Chrome --> Source) <br>
        Developer Tools possono espandere i file minificati <br>

        <h2>Minification Tools</h2>
        minifier.org<br>
        npmjs.com uglify-js, uglify-js-es6<br>

        <script>
        document.write("<h1>hello world</h1>"); // output nel documento
        window.alert("Questo è un alert !!!");  // popup
        window.prompt("Inserisci il tuo nome");  // input (Prompt)
        </script>

</body>
        <script type="text/javascript">
        // inline javascript dopo il body, viene eseguito al termine del caricamento della pagina
            nomeFunzione();           
        </script>

        <!-- script richiamati da file esterno dopo il body -->
        <script type="text/javascript" src="fileEsterno5.js"></script>
        

        <script type="text/javascript">
            console.log();
            console.info();
            console.error();
        </script>

</html>
```

Fonti:

- https://www.lynda.com/JavaScript-tutorials/JavaScript-Essential-Training by Morten Rand-Hendriksen on Lynda.com
- Programmare con JavaScript dalle basi ad Ajax di Ivan Venuti - Edizioni FAG Milano - 2010

varie:

- OnClick Academy JavaScript Fundamentals