# ILocalizationService Interface

[`chsxf\MFX\Services`](API-Namespace-Services)

```php
interface ILocalizationService
```

## Summary

Localization service interface

Since `2.0`

## Methods

### bindTextDomain

```php
public abstract function bindTextDomain(string $key, string $path, string $charset = 'UTF-8')
```

Binds a new text domain

Since `2.0`

#### Parameters

| Name       | Type     | Description                             |
| ---------- | -------- | --------------------------------------- |
| `$key`     | `string` | Text domain key                         |
| `$path`    | `string` | Text domain path                        |
| `$charset` | `string` | Text domain charset (Defaults to UTF-8) |

---

### getLanguage

```php
public abstract function getLanguage(): string
```

Gets the current language from the current locale

Since `2.0`

#### Returns

`string` 

---

### getLocale

```php
public abstract function getLocale(): string
```

Gets the current locale from environment

Since `2.0`

#### Returns

`string` 

---

