La dichiarazione DOCTYPE informa lo user agent (di seguito browser per semplicità) del tipo di documento che sta per leggere, il browser *dovrebbe* quindi interpretarlo in base alla dichiarazione fatta, il più delle volte si vuole che il browser utilizzi lo standard ufficiale e non delle interpretazioni proprietarie, altre volte si potrebbe volere indicare uno specifico tipo di documento come per l'XHTML.

DOCTYPE può essere scritto sia maiuscolo che minuscolo.

Riferimento ufficiale: https://www.w3.org/QA/2002/04/valid-dtd-list.html

La dichiarazione DOCTYPE per HTML5 è la seguente:
```html
<!DOCTYPE html>
```
Il tag *html* di apertura del documento HTML dovrebbe essere accompagnato dall'attributo *lang*, molto utile per gli screen readers e per i traduttori.
```html
<html lang="it">
```
Il tag *head* serve per contenere una serie di informazioni sul documento stesso e per richiamare risorse esterne come i fogli di stile e gli script.
```html
<head>
```
Il tag *meta* permette di dare molte informazioni utili al browser, come:
- che tipo di codifica dei caratteri bisogna utilizzare per il rendering della pagina (per la gran parte delle lingue occidentali è l'*utf-8*), il tag meta del charset deve essere lasciato entro i primi 1024 byte del file
- viewport
- una breve descrizione del contenuto della pagina, sarà utilizzata dai motori di ricerca (al 99% utilizzato nei risultati di ricerca) e da qualsiasi altro strumento che la prenda in considerazione
```html
    <meta charset="utf-8">  <!-- lasciare entro i primi 1024 byte -->
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <meta name="description" content="Descrizione della pagina">
```
Il tag *title* contiene il titolo della pagina che sarà utilizzato come titolo della finestra/scheda nel browser, come titolo del bookmark quando il link è salvato tra i preferiti del browser, sarà letto dai motori di ricerca e al 99% utilizzato come titolo della pagina nei risultati di ricerca e da qualsiasi altro strumento che lo prenda in considerazione.
```html    
    <title>Titolo della pagina</title>
```
```html 
    <base href="http://nomedominio.ext/percorso/">
    <link rel="stylesheet" href="../../lib/cssLLreset/LLreset.css">
    <style>
        .elemento-tag {
            color: red;
            font-weight: bold;
            background-color: yellow;
        }
    </style>

</head>
```
Il tag *body* contiene il documento vero e proprio.
```html   
<body>
    <p>Content models <br>
        HTML4: block, inline<br>
        HTML5:flow, metadata, embedded, interactive, heading, phrasing, sectioning.
    </p>
```
I tag *P* servono per racchiudere paragrafi di testo. Il tag di chiusura può essere tralsciato, MA NON è una buona abitudine, per scrivere un buon codice è meglio chiudere sempre i tag che hanno il tag di chiusura!
```html 
    <p>Questo è un <span class="elemento-tag">paragrafo</span> tag in <span class="elemento-tag">body</span>.</p>
```
I tag *BR* servono per andare forzatamente a capo, ad esempio per dividere in due una frase slogan. NON devono essere usati per creare spazio tra le righe o tra elementi.
```html 
    <p>Questo è un paragrafo<br> con tag BR <br> per andare a capo.</p>
```
I tag *EM* e *STRONG* servono per dare rispettivamente enfasi e importanza logica a una o più parole.
```html 
<p><em>Questo è fantastico ;) !</em></p>
<p><strong>Questo è davvero importante</strong>!</p>
```
HTML5 ha reintrodotto i tag *I* e *B*, servono per dare enfasi e importanza visiva a una o più parole.
```html 
<p><em>This<em> è un termine inglese!</em></p>
<p><b>Questo</b> è da mettere in evidenza.</p>
```

```html 
    <header class="testatapg">
        <p>Questo è un <span class="elemento-tag">paragrafo</span> tag in <span class="elemento-tag">header</span>.</p>
        <div class="logopg"></div>
        <nav class="menupg"></nav>
    </header>

    <main class="corpopg" role="main">
```
I tag *Hx* servono per i titoli delle varie sezioni del documento, creano una struttura gerarchica, dal principale H1 al più specifico H6.
```html         
        <h1>Titolo H1</h1>
        <h2>Titolo H2</h2>
        <h3>Titolo H3</h3>
        <h4>Titolo H4</h4>
        <h5>Titolo H5</h5>
        <h6>Titolo H6</h6>        <p>Questo è un <span class="elemento-tag">paragrafo</span> tag in <span class="elemento-tag">main</span>.<br> Lorem
            ipsum dolor sit amet, consectetur adipisicing elit. Distinctio aliquid at modi fugiat non eligendi consequatur
            cupiditate pariatur, voluptas placeat? Aperiam consequatur vel odit expedita dolor commodi quae facilis qui!<br><span>Questo è un elemento <span class="elemento-tag">span</span>.</span>
        </p>
        <p lang="us">This is a paragraph with lang attribute set to us, this helps screen readers to correctly pronounce the text.</p>
        <hr>
        <section>
            <ol>
                <li>lista ol 1</li>
                <li>lista ol 2</li>
                <li>lista ol 3</li>
                <li>lista ol 4</li>
                <li>lista ol 5</li>
            </ol>
            <hr>
            <ul>
                <li>lista ul 1</li>
                <li>lista ul 2</li>
                <li>lista ul 3</li>
                <li>lista ul 4</li>
                <li>lista ul 5</li>
            </ul>
        </section>
        <hr>
        <section><address>Questo è un elemento <span class="elemento-tag">address</span></address> in section.</section>
        <hr>
        <section>
            <p>Questo è un paragrafo in <span class="elemento-tag">section</span> tag.</p>
            <hr>
            <article>
                <p>Questo è un paragrafo in <span class="elemento-tag">article</span> tag.</p>
            </article>
        </section>
        <hr>
        <section>
            <pre>Questo è un testo  in <span class="elemento-tag">pre</span> tag.
Lorem ipsum dolor sit amet, consectetur adipisicing elit. Distinctio aliquid at modi fugiat non eligendi consequatur
cupiditate pariatur, voluptas placeat? Aperiam consequatur vel odit expedita dolor commodi quae facilis qui!</pre>
            <code>Questo è un <span class="elemento-tag">code</span> tag.</code><br>
            <samp>Questo è un <span class="elemento-tag">samp</span> tag.</samp><br>
            <var>Questo è un <span class="elemento-tag">var</span> tag.</var><br>
            <kbd>Questo è un <span class="elemento-tag">kbd</span> tag.</kbd><br>
            <sup>Questo è un <span class="elemento-tag">sup</span> tag.</sup><br>
            <sub>Questo è un <span class="elemento-tag">sub</span> tag.</sub><br>
        </section>
        <hr>
        <section>
            <blockquote>Questo è un <span class="elemento-tag">blockquote</span> tag. In una terra lontana, dietro le montagne Parole,
                lontani dalle terre di Vocalia e Consonantia, vivono i testi casuali. ‐ <cite>Questo è un <span class="elemento-tag">cite</span> tag.<a href="http://autore.aaa/Autore">Autore</a></cite></blockquote>
            <hr>
            <q>Questo è un <span class="elemento-tag">q</span> tag. In una terra lontana, dietro le montagne Parole,
                lontani dalle terre di Vocalia e Consonantia, vivono i testi casuali. ‐ <cite>Questo è un <span class="elemento-tag">cite</span> tag.<a href="http://autore.aaa/Autore">Autore</a></cite></q>
        </section>
        <hr>
        <section>
            <dl>
                <dt>Questo è un <span class="elemento-tag">dt</span> tag.<dfn>Questo è un <span class="elemento-tag">dfn</span> tag.</dfn></dt>
                <dd>... Questo è un <span class="elemento-tag">dd</span> tag. vocabolo o locuzione ...</dd>
            </dl>
        </section>
        <hr>
        <section>
 ```
 Il tag *img* serve per inserire immagini nel contenuto, gli attributi widht e height sono importanti per il rendering della pagina e l'attributo alt per fornire informazioni extra ad esempio agli screen reader.
 ```html
            <figure>
                <img src="autore.jpeg" alt="Autoritratto dell'autore del testo.">
                <figcaption>Questo è un <span class="elemento-tag">figcaption</span> tag in un <span class="elemento-tag">figure</span>                    tag.
                </figcaption>
            </figure>
        </section>
        <hr>
        <section>
            <div>
                Questo è un <span class="elemento-tag">div</span> tag.
            </div>
        </section>
        <hr>
        <section>
```
Il tag *A* serve per creare collegamenti
- assoluti o relativi
- ancore interne o esterne
- a indirizzi email, email
- a numeri di telefono
- si possono aprire anche in nuove finestre o in una specifica finestra
- a documenti con opzione solo download e nome dell'allegato specificato

```html
            <a href="#">Questo è un <span class="elemento-tag">a</span> tag.</a>
        </section>
        <hr>
        <section>
            <em>Questo è un <span class="elemento-tag">em</span> tag.</em><br>
            <i>Questo è un <span class="elemento-tag">i</span> tag.</i><br>
            <u>Questo è un <span class="elemento-tag">u</span> tag.</u><br>
            <b>Questo è un <span class="elemento-tag">b</span> tag.</b><br>
            <mark>Questo è un <span class="elemento-tag">mark</span> tag.</mark><br>
            <strong>Questo è un <span class="elemento-tag">strong</span> tag.</strong><br>
            <small>Questo è un <span class="elemento-tag">small</span> tag.</small><br>
            <abbr>Questo è un <span class="elemento-tag">abbr</span> tag.</abbr><br>
            <time>2017-08-14</time> Questo è un <span class="elemento-tag">time</span> tag.
            <ins>Questo è un <span class="elemento-tag">ins</span> tag.</ins><br>
            <del>Questo è un <span class="elemento-tag">del</span> tag.</del>
        </section>
        <hr>
        <section><img src="../../lib/img/loghi/Logo.png" alt="">
        </section>
        <hr>
        <section>
            <table>
                <thead>
                    <tr>
                        <th>th</th>
                        <th>th</th>
                    </tr>
                    <tr>
                        <th>th</th>
                        <th>th</th>
                    </tr>
                </thead>
                <tbody>
                    <tr>
                        <td>td</td>
                        <td>td</td>
                    </tr>
                    <tr>
                        <td>td</td>
                        <td>td</td>
                    </tr>
                    <tr>
                        <td>td</td>
                        <td>td</td>
                    </tr>
                </tbody>
                <tfoot>
                    <tr>
                        <td>td footer</td>
                        <td>td footer</td>
                    </tr>
                </tfoot>


            </table>
        </section>
        <hr>
        <section>
            <h2>Caratteri speciali>
                <p>HTML entities...</p>
                <p>&nbsp;</p>
        </section>
        <hr>
        <section>Form
            <form action="">
                <label for="">Input</label><input type="text">
                <label for="">button</label><button>Pulsante</button>
                <select name="Selezione" id="Selezione">Selezione</select>

                <textarea name="name" rows="8" cols="80"></textarea>
            </form>
        </section>
    </main>
    <hr>
    <aside>Questo è un paragrafo in <span class="elemento-tag">aside</span> tag.
    </aside>
    <hr>
    <footer class="piepg">Questo è un paragrafo in <span class="elemento-tag">footer</span> tag.</footer>

</body>

</html>
```
