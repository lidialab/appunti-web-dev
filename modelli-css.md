```css
/* BOX MODEL impostato a BORDER BOX */
html {
   box-sizing: border-box;
}
*, *:before, *:after {
   box-sizing: inherit;
}

/* CLEARFIX IE8+ */
.clearfix:after {
  content: "";
  display: table;
  clear: both;
}
```


**Link di riferimento:**

Box Model [https://www.paulirish.com/2012/box-sizing-border-box-ftw/](https://www.paulirish.com/2012/box-sizing-border-box-ftw/)
CanIuse Box-Sizing [http://caniuse.com/#search=box-sizing](http://caniuse.com/#search=box-sizing)

Clearfix [https://www.sitepoint.com/clearing-floats-overview-different-clearfix-methods/](https://www.sitepoint.com/clearing-floats-overview-different-clearfix-methods/) e [https://css-tricks.com/snippets/css/clear-fix/](https://css-tricks.com/snippets/css/clear-fix/)









