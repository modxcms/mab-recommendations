# MAB-01: Replace 3rd Party Libraries in Core with Composer Dependencies

The MODX Advisory Board recommends the MODX Project replace all 3rd party code in the core of MODX Revolution 3.x with appropriate Composer dependencies.

* **Editor:** Jason Coward
* **First published draft:** October 20, 2016
* **Accepted:** December 8, 2016 with 14 votes in favour


## Goal of Recommendation

To remove all 3rd party code directly committed to the MODX core, making it easier to update and manage 3rd party dependencies.


## Relevant Recommendations

 * [DRAFT] Refactor MODX Revolution 3.x as Slim 3.x App


## Recommendation

The core of MODX Revolution 3.x contains a number of 3rd party dependencies that have been directly committed to the repository. These should all be replaced by an equivalent Composer dependency where possible. In cases where there is no equivalent available via Composer, those dependencies should be replaced with an appropriate library that is available via Composer and any dependent code refactored for the new library.

Following is a list of 3rd party dependencies committed to the MODX core.

* AWS
* phpmailer
* phpthumb
* smarty
