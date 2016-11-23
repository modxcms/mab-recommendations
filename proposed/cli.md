# MODX CLI/console

* Status: DRAFT
* Editor: Romain Tripault


## Goal of Recommendation

Provide some CLI tool for MODX CMS


## Recommendation

The idea is to provide some CLI tool for developers & system administrators to rely on (as well as CI/CD platforms).
Developers should be able to ship their custom build commands (with their extras/components or independently).
We could also provide some kind of "generators" to help developers scaffold their custom development (thinking CMPs).

The base tool could ship a few critical commands (install the CMS, upgrade the CMS, install components/extras), leaving 
room for the community to come up with additional commands.

Some commands/use cases ideas:

* cache warm up
* deploying to a remote environment (MODX Cloud, dedicated server...)
* move a standard installation to a "core outside webroot" one
* put a site/context "offline" for maintenance
* iterate a folder recursively to create appropriate static elements (snippets/chunks...)
* install/switch a theme

Some existing tools in our community:

* Gitify - https://github.com/modmore/gitify
* GPM - https://github.com/theboxer/Git-Package-Management
* Teleport - https://github.com/modxcms/teleport
* MODX CLI https://github.com/alanpich/modx-cli
* MODX Shell - https://github.com/meltingmedia/MODX-Shell
* xPDO - https://github.com/modxcms/xpdo

Other platforms/CMS/Frameworks tools: 

* drush - http://www.drush.org/
* drupal console - http://drupalconsole.com/
* WP CLI - http://wp-cli.org/
* Symfony console - http://symfony.com/doc/current/components/console.html
* Laravel Artisan - https://laravel.com/docs/master/artisan
* Composer - https://getcomposer.org/

