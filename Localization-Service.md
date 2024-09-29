Localization (L10n) management in MFX relies on the [gettext](https://www.php.net/manual/en/book.gettext.php) extension. So, even if this is a pretty straightforward process within MFX, you will need basic knowledge of how the extension works.

Control of localizations is handled through the Localization Service, which implements the `ILocalizationService` interface.

## What is Gettext?

[GNU gettext](https://www.gnu.org/software/gettext/manual/gettext.html) is a tool that allows developers to implement translations directly into their applications, as close as possible to the actual feature that uses them.

Thanks to a specific syntax, gettext is able to extract original texts into a `.po` file that acts as a database from translations. Once translated, this file is compiled into another binary `.mo` file that is finally used by gettext to retrieve translated strings that will be used in the final product.

For example:

```php
echo _('My translated text');
// Will print evntually
// - "My translated text" if the locale is en_US
// - "Mon texte traduit" if the locale is fr_FR
// ... and so on for other locales
```

`_` is an alias of the [`gettext`](https://www.php.net/manual/en/function.gettext.php) function. You can use either of those.

## `.po` and `.mo` files

When working with PHP files, extracting translations into a `.po` file is straightforward thanks to the [`xgettext`](https://www.gnu.org/software/gettext/manual/gettext.html#Template) utility.

However, MFX makes also use of Twig template files that are not recognized by `xgettext`. Fortunately, we have developed a solution for that in the [chsxf/TwigTools](https://github.com/chsxf/TwigTools) package MFX depends on. You can find more information on how to extract translation from template files [on this page](https://github.com/chsxf/TwigTools/blob/main/README_Gettext.md).

Multiple `.po` files may exist inside a single MFX app (within a specific "domain"). If you have multiple localization domains, you must generate one `.po` file (and therefore one `.mo` file) per domain and per locale.

To configured multiple text domains, please refer to the corresponding [configuration directives](Configuration-Directives#localization-l10n).

### Translating

Once your `.po` files have been generated, you have to translate them (either directly or through an external translation service at your convenience). Then you compile `.mo` files and put them right besides the corresponding `.po` files.

We recommend using [poedit](https://poedit.net/) as your translation software, notably because it embarks `xgettext` directly and you won't need any other dependency to translate your app.

However many other applications or online services handle `.po` files perfectly as well.

### File Locations

In your configuration file, you can define one or more localization domains. If you plan to support localization, it is recommended to define at least the `__default` domain which does not require any additional parameter for your translations.

To each localization domain is associated a base path (for example `application/messages`). The `.po` and `.mo` files of a localization domain are located in the `<locale>/LC_MESSAGES` subfolder (for example `fr_FR/LC_MESSAGES`). The files are then named after the localization domain.

For example, for the `__default` domain, you would get the following folder structure:

```
📂 application
    📂 messages
        📂 fr_FR
            📂 LC_MESSAGES
                📝 __default.po
                📄 __default.mo
        📂 es_ES
            📂 LC_MESSAGES
                📝 __default.po
                📄 __default.mo
    ...
```

## Localizing Templates

As stated above, MFX uses the chsxf/TwigTools package which provides a Gettext extension for Twig. You can then use the exact same gettext functions in your templates as you would in your PHP files.

For example, the error manager's templates use the [`dgettext`](https://www.php.net/manual/en/function.dgettext.php) function to translate a "Close" label from the `mfx` translation domain.

```twig
<a href="#" class="mfx-hide-parent-on-click">{{ dgettext('mfx', 'Close') }}</a>
```

The extension also defines several aliases for functions other than `gettext`. However, these aliases are only usable inside Twig tempaltes.

Please refer to [the chsxf/TwigTools documentation](https://github.com/chsxf/TwigTools/blob/main/README_Gettext.md) for more information.

## Accessing the Current Locale and Language

The Localization Service provides methods to know what language and locale are currently used for the request. Use the following methods:

```php
function getLocale(): string;

function getLanguage(): string;
```

> [!NOTE]
> The returned language will conform to the ISO 639-1 alpha-2 norm.
>
> The returned locale will conform to the following pattern: `<language_code>_<COUNTRY_CODE>` (where the `COUNTRY_CODE` conforms to the ISO 3166-1 alpha-2 norm).
