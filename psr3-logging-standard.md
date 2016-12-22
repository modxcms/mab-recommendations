# PSR-3 Logging Standard

The PSR-3 Standard from the PHP-FIG contains an interface for a standardized logging solution. This standard has been widely adopted throughout the industry, and it is recommended that MODX 3 adopts this standard, and its most common implementation Monolog. This will benefit the project in terms of reduced code maintenance, a more powerful logging solution, and an increased appeal for developers.  

* **Editor:** Mark Hamstra
* **First published draft:** November 23, 2016
* **Accepted:** December 21, 2016 with 11 votes in favour

## Goal of Recommendation

The adoption of the PSR-3 Standard in MODX 3, and implementation of that standard with the Monolog library. This achieves the following goals:

- Allows the logging implementation to be easily switched and configured through a dependency container. The dependency container has been discussed in “Refactor MODX Revolution 3.x as Slim 3.x App” and “Adopt PHP-DI as Dependency Injection Container” recommendations. 
- More flexible logging compared to the MODX 2.x implementation, for example by being able of specifying where log messages of certain severities are logged, including with third party services or log aggregators and email notifications.

## Relevant Recommendations

- Slim Refactor, by Jason Coward
- Replace 3rd Party Libraries with composer dependencies, by Jason Coward

## Recommendation

The PSR-3 Logging Standard defines a common interface for logging implementations. This makes it possible to implement logging into a dependant application, without needing to know specifics about the logger configuration or implementation. 

Through the use of a dependency injection container (discussed in the “Refactor MODX Revolution 3.x as Slim 3.x App” and “Adopt PHP-DI as Dependency Injection Container” recommendations), it will be possible to define arbitrary implementations of the PSR-3 standard, and to configure those on an installation-by-installation basis. 

### Default Implementation

The default PSR-3 implementation in MODX 3 should work similar to the logger in MODX 2, while allowing extensive customisation and flexibility. 

The default implementation should at least:

- use the `monolog/monolog` package, included as composer dependency and autoloaded through the proposed dependency injection container. The `monolog/monolog` package is preferred due to its popularity in the PHP community (38.8M installations on Packagist) and abundance of third party packages providing handlers and formatters.
- log all errors with a specified severity (`log_level` system setting, defaulting to error-level logs) or higher into a centralised `error.log` file located in `core/cache/logs`.

Additional functionality and configuration may be implemented in the default configuration.

### Backwards Compatibility

There are a few concerns related to backwards compatibility in implementing this recommendation. 

- PSR-3 states that the `log()` method is called on a `logger` interface. In MODX 2.x a `log()` method is provided on the xPDO/modX object. To preserve backwards compatibility and ease a transition to MODX 3, the xPDO/modX `log()` method should keep its existing signature, and translate that to the proper method call on the logger interface in the dependency injection container. 
- The MODX 2.x `log()` method contains logic related to the so-called Registry. This is used in package installations, cache clearing and some third party extras to provide feedback in long-running processes. A different method to replace this behaviour should be implemented in MODX 3.x. 

