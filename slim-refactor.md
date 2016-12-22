# Refactor MODX Revolution 3.x as Slim 3.x App

The MODX Advisory Board recommends the MODX Project to refactor the core MODX classes and model on top of Slim 3.x to accelerate the modernization of the core codebase.

* **Editor:** Jason Coward
* **First published draft:** October 20, 2016
* **Accepted:** December 8, 2016 with 14 votes in favour

## Goal of Recommendation

By refactoring MODX Revolution 3.x on top of Slim 3.x, MODX would instantly gain the benefits of an outstanding PHP microframework as a new foundation for future advancements and improve maintainability. By simply adapting Revolution's modX class as a Slim App instead of extending xPDO for this foundation, PSR-4 autoloading, proper dependency injection, PSR-7 HTTP messaging standards and the flexible middleware-centric architecture would automatically become part of the MODX core. Much backwards compatibility can be maintained while effectively jump starting the modernization of the existing codebase.


## Relevant Recommendations

* [DRAFT] Refactor Data Model using xPDO 3.x
* [DRAFT] Adopt PHP-DI as Dependency Injection Container
* [DRAFT] Replace 3rd Party Libraries in Core with Composer Dependencies


## Recommendation

The Slim framework is one of the highest quality microframeworks in the PHP development world at this time. It implements more standards and is measurably more maintainable than any other framework available. By retrofitting the legacy MODX Revolution codebase on top of this framework, we can get a head start on modernizing the aging CMS and keeping it relevant for many years to come. Lack of contributions and difficulty in innovating on the legacy codebase is making MODX less and less relevant as time marches on. 

By adopting a microframework that clearly exemplifies modern PHP best practices, core functionality could be more quickly swapped out in more areas without the extensive proprietary knowledge currently required. This could encourage adoption and development by a larger group of PHP developers, many of which already respect Slim. This could help increase the quantity and quality of contributions to the core, and encourage the development of higher quality extras for end-users to take advantage of.

Following is a list of features and benefits adopting Slim could instantly bring to MODX.

* Small, well-architected microframework for utilizing best-in-class libraries.
* Composer-ready.
* PSR-4 autoloading capabilities.
* Dependency Injection Container based on proposed PSR-11 standards.
* PSR-7 Http Messaging standards for Requests and Responses.
* Flexible PSR-7 Middleware architecture.
* Fast, parameterized routing via FastRoute, a popular PHP routing library.
* A strong foundation for more maintainable code ( see https://twitter.com/ykanellopoulos/status/789124726417416192 ).
* Would make it prudent to join PHP-FIG as a member project.
