# L10nManager Class

[`chsxf\MFX\L10n`](API-Namespace-L10n)

```php
class L10nManager
```

## Summary

Helper class for managing localization

Since `1.0`

## Methods

### bindTextDomain

```php
public static function bindTextDomain(string $key, string $path, string $charset = 'UTF-8')
```

Binds a new text domain

Since `1.0`

#### Parameters

| Name       | Type     | Description                             |
| ---------- | -------- | --------------------------------------- |
| `$key`     | `string` | Text domain key                         |
| `$path`    | `string` | Text domain path                        |
| `$charset` | `string` | Text domain charset (Defaults to UTF-8) |

---

### getLanguage

```php
public static function getLanguage(): string
```

Gets the current language from the current locale

Since `1.0`

#### Returns

`string` 

---

### getLocale

```php
public static function getLocale(): string
```

Gets the current locale from environment

Since `1.0`

#### Returns

`string` 

---

