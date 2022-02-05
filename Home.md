## ❓ What is MFX?

MFX is a full-stack PHP framework originally designed to serve as a project basis for Cheese Burgames, a now-defunct french independant video game studio. The first version, originally called php-micro-framework has been introduced in 2013 and matured in 2016. With time, MFX has evolved into a complete framework for external developments.

It can be used as the core of any regular website or API.

## 📄 License

MFX is released under the [MIT license](https://github.com/chsxf/mfx/LICENSE).

## ⚙️ System Requirements

* PHP 8.1+ with enabled [gettext](https://www.php.net/manual/fr/book.gettext.php) extension
* Apache with `mod_rewrite` module enabled
* Any database management system compatible with PDO (MySQL, MariaDB, PostgreSQL, ...) if you plan to use database storage (see [PDO documentation](https://www.php.net/manual/en/book.pdo.php) for more information)

## ⛓ Dependencies

* **Twig**\
  Template engine\
  https://twig.symfony.com/
* **PDO database manager**\
  PDO extended with some nice utility functions\
  https://packagist.org/packages/chsxf/pdo-database-manager
* **Twig Tools**\
  Set of useful extensions for Twig (switch blocks, lazy blocks, support for gettext inside the templates)\
  https://packagist.org/packages/chsxf/twig-tools

## 🚀 Getting Started

Go to [this page](Getting-Started) to start using MFX.

## 📝 Complete documentation

To access a deeper and more complete documentation on the design and usage of MFX, go to the [[Framework Reference]].

## 🗓 Planned Improvements

*(This list is not prioritized)*

* [x] Making it compatible with Composer
* [ ] Adding a setup script
* [ ] Making it compatible with nginx
* [ ] Making it possible to replace the default router with a custom one
* [ ] Improving `DatabaseUpdater` reliability and error resilience
* [x] Removing php-gettext library dependency (making gettext extension mandatory)
* [x] Updating Twig to version 2.x

## 💥 Known Issues

*(This list is not prioritized)*

* [ ] The post-route callback may not be called with some request results
* [ ] Pre-conditions should be validated before calling pre-route callbacks
