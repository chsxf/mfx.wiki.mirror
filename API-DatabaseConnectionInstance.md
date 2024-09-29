# DatabaseConnectionInstance Class

[`chsxf\MFX`](API-Namespace-chsxf_MFX)

```php
class DatabaseConnectionInstance extends chsxf\PDO\DatabaseManager
```

## Summary

Instance of a database connection

Since `2.0`

## Methods

### __construct

```php
public function __construct(string $serverConfigurationKey, string $dsn, ?string $username = null, ?string $password = null, ?array $options = null, bool $useDatabaseErrorLogging = false)
```

Constructor

See `chsxf\PDO\DatabaseManager::__construct()`

Since `2.0`

#### Parameters

| Name                       | Type     | Description                                                                                 |
| -------------------------- | -------- | ------------------------------------------------------------------------------------------- |
| `$serverConfigurationKey`  | `string` | Server configuration key (matches the server keys declared in the configuration directives) |
| `$dsn`                     | `string` | Data Source Name (ie mysql:host=localhost;dbname=mydb)                                      |
| `$username`                | `string` | Username                                                                                    |
| `$password`                | `string` | Password                                                                                    |
| `$options`                 | `array`  | Driver options                                                                              |
| `$useDatabaseErrorLogging` | `bool`   | Is set, errors will be logged in the database. False by default                             |

---

### getServerConfigurationKey

```php
public function getServerConfigurationKey()
```

Returns the server configuration key

Since `2.0`

#### Returns

`string` 

---

