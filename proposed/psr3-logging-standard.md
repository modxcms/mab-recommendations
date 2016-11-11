# PSR-3 Logging Standard

Note: This recommendation is a DRAFT for consideration of the MODX Advisory Board. 

The PSR-3 Standard from the PHP-FIG contains an interface for a standardized logging solution. This standard has been widely adopted throughout the industry, and it is recommended that MODX 3 adopts this standard, and its most common implementation Monolog. This will benefit the project in terms of reduced code maintenance, a more powerful logging solution, and an increased appeal for developers.  

Editor: Mark Hamstra

First published draft: Not yet reviewed/published.


## Goal of Recommendation

The adoption of the PSR-3 Standard in MODX 3, and implementation of that standard with the Monolog library. This achieves the following goals:

- Allows the logging implementation to be easily switched and configured through a dependency container. The dependency container has been discussed in “Refactor MODX Revolution 3.x as Slim 3.x App” and “Adopt PHP-DI as Dependency Injection Container” recommendations. 
- More flexible logging compared to the MODX 2.x implementation, for example by being able of specifying where log messages of certain severities are logged, including with third party services or log aggregators and email notifications.

## Relevant Recommendations

- Slim Refactor, by Jason Coward
- Replace 3rd Party Libraries with composer dependencies, by Jason Coward

## Recommendation

The PSR-3 Logging Standard defines a common interface for logging implementations. This makes it possible to implement logging into a dependant application, without needing to know specifics about the logger configuration. 

Through the use of a dependency injection container (discussed in the “Refactor MODX Revolution 3.x as Slim 3.x App” and “Adopt PHP-DI as Dependency Injection Container” recommendations), it will be possible to define arbitrary implementations of the PSR-3 standard, and to configure those on an installation-by-installation basis. 

The default PSR-3 implementation in MODX 3 needs to work out of the box in a similar fashion as the logging today, while allowing extensive customisation and flexibility for the more demanding users. For the out of the box implementations, the following guidelines were drafted:

- The included PSR-3 logging library should be the `monolog/monolog` package, included through Composer/Packagist and autoloaded. The reason for the preference of `monolog/monolog` over other PSR-3 compliant packages is its popularity in the PHP community as evidenced on Packagist; out of 40 million installations of the PSR-3 interfaces (`psr/log`), `monolog/monolog` has 38.8 million installations. 
- The default configuration of the logger should be similar to the logging present in MODX 2.x. This mean the default configuration should log all messages that hold at least the severity configured in the `log_level` system setting to a single log file located in `core/cache/logs/error.log`.

Implementing the PSR-3 standard into MODX means a few changes, some of which may break backwards compatibility. 

- PSR-3 mandates that the log() method on an instance of a logger interface is called. In the current MODX 2.x situation, the log() method is located on the xPDO object instead. With the introduction of a dependency injection container the logger can be loaded as necessary, however existing code will need to be adjusted. To preserve backwards compatibility, a magic `__call()` method, or not-as-magical `log()` method can be provided on the new modX object to forward the method call to the new logger instance. 
- The current `log()` method contains some behaviour specific to MODX where it can be used to store information in the registry. This is used in console windows, such as installing packages, to present running output of a long-running process which is filled through the log method. This behaviour is not present in the PSR-3 implementation, so would be a breaking change that needs to be handled separately. In the MODX core, this is used for package installations and clearing the cache. Few extras exist that implement a similar functionality, but those will need to be updated. 

