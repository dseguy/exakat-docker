When using a break, the argument of the operator must be a positive non-null integer literal or be omitted.

Other values were acceptable in PHP 5.3 and previous version, but this is now reported as an error.

<?php
    // Can't break $a, even if it contains an integer.
    $a = 1;
    for($i = 0; $i < 10; $i++) {
        break $a;
    }

    // can't break on float
    for($i = 0; $i < 10; $i++) {
        for($j = 0; $j < 10; $j++) {
            break 2.2;
        }
    }

?>

