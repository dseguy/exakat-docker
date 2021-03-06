Calling global (or $GLOBALS) in methods is slower and less testable than setting the global to a property, and using this property.

Using properties is slightly faster than calling global or $GLOBALS, though the gain is not important. 

Setting the property in the constructor (or in a factory), makes the class easier to test, as there is now a simple point of configuration.

<?php 

// Wrong way
class fooBad {
    function x() {
        global $a;
        $a->do();
        // Or $GLOBALS['a']->do();
    }
}

class fooGood {
    private $bar = null;
    
    function __construct() {
        global $bar; 
        $this->bar = $bar;
        // Even better, do this via arguments
    }
    
    function x() {
        $this->a->do();
    }
}

?>

