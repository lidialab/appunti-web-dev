La dichiarazione DOCTYPE informa il client del tipo di documento che sta per leggere, il browser *dovrebbe* quindi interpretarlo in base alla dichiarazione fatta, il più delle volte si vuole che il browser utilizzi lo standard ufficiale e non delle interpretazioni proprietarie, altre volte si potrebbe volere indicare uno specifico tipo di documento come per l'XHTML.

DOCTYPE può essere scritto sia maiuscolo che minuscolo.

Riferimento ufficiale: https://www.w3.org/QA/2002/04/valid-dtd-list.html

La dichiarazione DOCTYPE per HTML5 è la seguente:
```html
<!DOCTYPE html>
```

```html
<html lang="it">

<head>
    <title>Titolo della pagina</title>
    <meta charset="utf-8">  <!-- lasciare entro i primi 1024 byte -->
    <meta name="viewport" content="width=device-width, initial-scale=1">
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
<!-- revisionato fino a qua -->
<body>
    <p>Questo è un <span class="elemento-tag">paragrafo</span> tag in <span class="elemento-tag">body</span>.</p>

    <header class="testatapg">
        <p>Questo è un <span class="elemento-tag">paragrafo</span> tag in <span class="elemento-tag">header</span>.</p>
        <div class="logopg"></div>
        <nav class="menupg"></nav>
    </header>

    <main class="corpopg" role="main">
        <h1>Titolo H1</h1>
        <h2>Titolo H2</h2>
        <h3>Titolo H3</h3>
        <h4>Titolo H4</h4>
        <h5>Titolo H5</h5>
        <h6>Titolo H6</h6>
        <p>Questo è un <span class="elemento-tag">paragrafo</span> tag in <span class="elemento-tag">main</span>.<br> Lorem
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
