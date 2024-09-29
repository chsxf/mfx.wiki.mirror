# IConfigService Interface

[`chsxf\MFX\Services`](API-Namespace-Services)

```php
interface IConfigService
```

## Summary

Configuration service interface

Since `2.0`

## Constants

```php
public const DEFAULT_DOMAIN = '__default';
```

Since `2.0`

## Methods

### getValue

```php
public abstract function getValue(string $property, mixed $default = null, ?string $domain = null): mixed
```

Gets the value of a configuration property

Since `2.0`

#### Parameters

| Name        | Type          | Description                                                                                 |
| ----------- | ------------- | ------------------------------------------------------------------------------------------- |
| `$property` | `string`      | Name of the propery                                                                         |
| `$default`  | `mixed`       | Default value if the property does not exist in the loaded configuration (Defaults to NULL) |
| `$domain`   | `string|null` | Domain name (defaults to NULL, which is the default domain)                                 |

#### Returns

`mixed` 

---

### hasValue

```php
public abstract function hasValue(string $property, ?string $domain = null): bool
```

Determines if a property has been loaded in the configuration

Since `2.0`

#### Parameters

| Name        | Type          | Description                                                 |
| ----------- | ------------- | ----------------------------------------------------------- |
| `$property` | `string`      | Name of the propery                                         |
| `$domain`   | `string|null` | Domain name (defaults to NULL, which is the default domain) |

#### Returns

`bool` true if the property exists in the loaded configuration, false either

---

### load

```php
public abstract function load(Config $configData, string $domain = 'self::DEFAULT_DOMAIN')
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
public abstract function tryGetValue(string $property, mixed &$outValue, ?string $domain = null): bool
```

Tries to get the value of a configuration property

Since `2.0`

#### Parameters

| Name        | Type          | Description                                                         |
| ----------- | ------------- | ------------------------------------------------------------------- |
| `$property` | `string`      | Name of the propery                                                 |
| `$outValue` | `mixed`       | Reference to the variable containing the property value if existing |
| `$domain`   | `string|null` | Domain name (defaults to NULL, which is the default domain)         |

#### Returns

`bool` true if the property exists in the loaded configuration, or false either

---

