Those strings looks like holding a variable. 

Single quotes and Nowdoc syntax may include $ signs that are treated as literals, and not replaced with a variable value. 

However, there are some potential variables in those strings, making it possible for an error : the variable was forgotten and will be published as such. It is worth checking the content and make sure those strings are not variables.

<?php

$a = 2;

// Explicit variable, but literal effect is needed
echo '$a is '.$a;

// One of the variable has been forgotten
echo '$a is $a';

// $CAD is not a variable, rather a currency unit
$total = 12;
echo $total.' $CAD';

// $CAD is not a variable, rather a currency unit
$total = 12;

// Here, $total has been forgotten
echo <<<'TEXT'
$total $CAD
TEXT;

?>
