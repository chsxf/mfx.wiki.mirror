# Config Class

[`chsxf\MFX`](API-Namespace-chsxf_MFX)

```php
class Config
```

## Summary

Singleton configuration management helper class

Since `1.0`

## Methods

### get

```php
public static function get(string $property, mixed $default = null): mixed
```

Gets the value of a configuration property

Since `1.0`

#### Parameters

| Name        | Type     | Description                                                            |
| ----------- | -------- | ---------------------------------------------------------------------- |
| `$property` | `string` | Name of the propery                                                    |
| `$default`  | `mixed`  | Default value if the property has not been provided (Defaults to NULL) |

#### Returns

`mixed` 

#### Throws

| Exception        | Reason                                                                    |
| ---------------- | ------------------------------------------------------------------------- |
| `ErrorException` | If the Config::load() function has not been executed at least once before |

---

### has

```php
public static function has(string $property): bool
```

Determines if a configuration property has been provided in the configuration file

Since `1.0`

#### Parameters

| Name        | Type     | Description         |
| ----------- | -------- | ------------------- |
| `$property` | `string` | Name of the propery |

#### Returns

`boolean` true if the property has been provided, false either

#### Throws

| Exception        | Reason                                                                    |
| ---------------- | ------------------------------------------------------------------------- |
| `ErrorException` | If the Config::load() function has not been executed at least once before |

---

### load

```php
public static function load(array $configData = array())
```

Loads configuration properties

Since `1.0`

#### Parameters

| Name          | Type    | Description |
| ------------- | ------- | ----------- |
| `$configData` | `array` | Config data |

---

### loadOnDomain

```php
public static function loadOnDomain(string $_domain, string $_path)
```

Loads configuration properties from a second configuration file into the specific domain

Since `1.0`

#### Parameters

| Name       | Type     | Description                                             |
| ---------- | -------- | ------------------------------------------------------- |
| `$_domain` | `string` | Domain under which configuration properties will be set |
| `$_path`   | `string` | Path of the configuration file to load                  |

---

