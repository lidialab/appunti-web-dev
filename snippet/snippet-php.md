# Snippet PHP
## money_format()
is undefined in Windows, because Win hasn't strfmon capabilities;
installare ..... php

```php
<?php

$number = 1234.56;
setlocale(LC_MONETARY,"en_US");
echo money_format("The price is %i", $number);

setlocale(LC_MONETARY,"it_IT");
echo money_format("Il prezzo è %i", $number);

?>
```
