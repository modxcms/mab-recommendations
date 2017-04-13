# MAB-02: Adopt PHP-DI as Dependency Injection Container

The MODX Advisory Board recommends the MODX Project adopt PHP-DI as the Dependency Injection Container for MODX Revolution 3.x.

* **Editor:** Jason Coward
* **First published draft:** October 20, 2016
* **Accepted:** December 8, 2016 with 14 votes in favour

## Goal of Recommendation

To adopt a flexible and powerful Dependency Injection Container so MODX Revolution 3.x can begin using a configurable dependency injection instead of the legacy approach of service location for MODX core services.


## Relevant Recommendations

 * [DRAFT] Refactor MODX Revolution 3.x as Slim 3.x App


## Recommendation

Taking advantage of proper dependency injection can foster a higher quality and more maintainable architecture for any modern software application. PHP-DI ( see http://php-di.org/ ) provides a powerful, and flexible dependency injection container that has been quick to follow and adopt the proposed PSR-11 Container standards. It supports a number of different forms of dependency injection which the diverse MODX ecosystem could utilize without forcing one approach on everyone in every situation.

Following is a list of features and benefits MODX would gain by adopting PHP-DI.

* Support for various forms of dependency injection:
    * Annotations — recommended for writing controllers in MVC apps and could be utilized by core when managing Resources, which are essentially controllers.
    * Constructor Injection — recommended for writing services.
    * Auto-Wiring — a recommended alternative when writing services where possible.
* Easy, expressive container configuration using PHP code.
* PHP-DI is well documented.
