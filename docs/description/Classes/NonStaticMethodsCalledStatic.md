Static methods have to be declared as such (using the static keyword). Then, 
one may call them without instantiating the object.

PHP 7.0, and more recent versions, yield a deprecated error : 'Non-static method A::B() should not be called statically' .

PHP 5 and older doesn't check that a method is static or not : at any point, you may call one
method statically : 

<?php
    class x {
        static public function sm( ) { echo __METHOD__.\n; }
        public public sm( ) { echo __METHOD__.\n; }
    } 
    
    x::sm( ); // echo x::sm 
?>

It is a bad idea to call non-static method statically. Such method may make use of special
variable $this, which will be undefined. PHP will not check those calls at compile time,
nor at running time. 

It is recommended to update this situation : make the method actually static, or use it only 
in object context.

Note that this analysis reports all static method call made on a non-static method,
even within the same class or class hierarchy. PHP silently accepts static call to any
in-family method.

<?php
    class x {
        public function foo( ) { self::bar() }
        public function bar( ) { echo __METHOD__.\n; }
    } 
?>

See also [static keyword](http://php.net/manual/en/language.oop5.static.php).

