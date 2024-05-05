## What is MFX?

MFX is a full-stack PHP micro-framework (hence "MFX"), designed to be used as the core of any regular website or API.

Originally created as a project basis for Cheese Burgames, a now-defunct french independant video game studio. The first version, previously called php-micro-framework was introduced in 2013 and matured in 2016. With time, MFX has evolved into a complete framework for external developments.

## License

MFX is released under the [MIT license](https://github.com/chsxf/mfx/LICENSE).

## System Requirements

- PHP 8.1+ with enabled [gettext](https://www.php.net/manual/fr/book.gettext.php) extension
- Apache with `mod_rewrite` module enabled
- Any database management system compatible with PDO (MySQL, MariaDB, PostgreSQL, ...) if you plan to use database storage (see [PDO documentation](https://www.php.net/manual/en/book.pdo.php) for more information)

## Dependencies

- **Twig**\
  Template engine\
  https://twig.symfony.com/
- **PDO database manager**\
  PDO extended with some nice utility functions\
  https://github.com/chsxf/pdo-database-manager
- **Twig Tools**\
  Set of useful extensions for Twig (switch blocks, lazy blocks, support for gettext inside the templates)\
  https://github.com/chsxf/TwigTools

## Getting Started

Go to [this page](Getting-Started) to start using MFX.

## Support

Development on MFX is still active. Even though the project is production-ready, new features and bugfixes will come eventually.

However, support is not guaranteed in any way. [Pull requests](https://github.com/chsxf/mfx/pulls) or [issues](https://github.com/chsxf/mfx/issues) are welcomed but you may wait for some time before getting any answer.

## Contributing to the Documentation

If you want to contribute to this documentation, please go to the [mirror repository](https://github.com/chsxf/mfx.wiki.mirror) and create issues or pull requests there.
