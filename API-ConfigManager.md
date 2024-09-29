# ConfigManager Class

[`chsxf\MFX`](API-Namespace-chsxf_MFX)

```php
final class ConfigManager implements Services\IConfigService
```

## Summary

Configuration directives manager, acting as the default configuration service implementation

Since `2.0`

## Methods

### __construct

```php
public function __construct()
```

Constructor

Since `2.0`

---

### getValue

```php
public function getValue(string $property, mixed $default = null, ?string $domain = null): mixed
```

Gets the value of a configuration property

Since `2.0`

#### Parameters

| Name        | Type          | Description                                                         |
| ----------- | ------------- | ------------------------------------------------------------------- |
| `$property` | `string`      | Path of the property we're trying to get the value of               |
| `$default`  | `mixed`       | Default value if the property has not been found (Defaults to NULL) |
| `$domain`   | `null|string` | Domain name (defaults to null, therefore using the default domain)  |

#### Returns

`mixed` 

---

### hasValue

```php
public function hasValue(string $property, ?string $domain = null): bool
```

Determines if a configuration property has been provided in the configuration file

Since `2.0`

#### Parameters

| Name        | Type          | Description                                                        |
| ----------- | ------------- | ------------------------------------------------------------------ |
| `$property` | `string`      | Path of the property we're trying to get the value of              |
| `$domain`   | `null|string` | Domain name (defaults to null, therefore using the default domain) |

#### Returns

`boolean` true if the property has been provided, false either

---

### load

```php
public function load(Config $configData, string $domain = 'self::DEFAULT_DOMAIN')
```

Loads configuration properties

Since `2.0`

#### Parameters

| Name          | Type     | Description |
| ------------- | -------- | ----------- |
| `$configData` | `Config` | Config data |
| `$domain`     | `string` | Domain name |

---

### tryGetValue

```php
public function tryGetValue(string $property, mixed &$outValue, ?string $domain = null): bool
```

Try getting a value from the currently loaded configuration directives

Since `2.0`

#### Parameters

| Name        | Type          | Description                                                        |
| ----------- | ------------- | ------------------------------------------------------------------ |
| `$property` | `string`      | Path of the property we're trying to get the value of              |
| `$outValue` | `mixed`       | Output value reference                                             |
| `$domain`   | `null|string` | Domain name (defaults to null, therefore using the default domain) |

#### Returns

`bool` <code>true</code> if the value exists, <code>false</code> either

#### Throws

| Exception         | Reason                                                                                        |
| ----------------- | --------------------------------------------------------------------------------------------- |
| `ConfigException` | if the requested domain is not loaded, or the property path or the domain uses invalid syntax |

---

