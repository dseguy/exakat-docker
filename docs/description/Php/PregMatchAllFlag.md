preg_match_all() has an option to configure the structure of the results : it is either by capturing parenthesis (by default), or by result sets. 

The second option is the most interesting when the following foreach() loop has to manipulate several captured strings at the same time. No need to use an index in the first array and use it in the other arrays.

<?php
$string = 'ababab';

// default behavior
preg_match_all('/(a)(b)/', $string, $r);
$found = '';
foreach($r[1] as $id => $s) {
    $found .= $s.$r[2][$id];
}

// better behavior
preg_match_all('/(a)(b)/', $string, $r, PREG_SET_ORDER);
$found = '';
foreach($r as $s) {
    $found .= $s[1].$s[2];
}

?>

The second syntax is easier to read and may be marginally faster to execute (preg_match_all and foreach).
