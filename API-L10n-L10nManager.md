# L10nManager Class

[`chsxf\MFX\L10n`](API-Namespace-L10n)

```php
final class L10nManager implements Services\ILocalizationService
```

## Summary

Helper class for managing localization

Since `1.0`

## Methods

### __construct

```php
public function __construct(Services\IConfigService $configService)
```

Constructor

Since `1.0`

#### Parameters

| Name             | Type             | Description             |
| ---------------- | ---------------- | ----------------------- |
| `$configService` | `IConfigService` | Config service instance |

---

### bindTextDomain

```php
public function bindTextDomain(string $key, string $path, string $charset = 'UTF-8')
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
public function getLanguage(): string
```

Gets the current language from the current locale

Since `2.0`

#### Returns

`string` 

---

### getLocale

```php
public function getLocale(): string
```

Gets the current locale from environment

Since `2.0`

#### Returns

`string` 

---

