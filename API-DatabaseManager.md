# DatabaseManager Class

[`chsxf\MFX`](API-Namespace-chsxf_MFX)

```php
final class DatabaseManager extends chsxf\PDO\DatabaseManager
```

## Summary

Database manager class

Since `1.0`

## Constants

```php
public const DEFAULT_CONNECTION = '__default';
```

## Methods

### __construct

```php
public function __construct(string $dsn, string $username, string $password, string $server = 'self::DEFAULT_CONNECTION')
```

Constructor

See `\PDO::__construct()`

Since `1.0`

#### Parameters

| Name        | Type     | Description                                            |
| ----------- | -------- | ------------------------------------------------------ |
| `$dsn`      | `string` | Data Source Name (ie mysql:host=localhost;dbname=mydb) |
| `$username` | `string` | Username                                               |
| `$password` | `string` | Password                                               |
| `$server`   | `string` | Server configuration key                               |

---

### close

```php
public static function close(DatabaseManager &$_manager)
```

Since `1.0`

#### Parameters

| Name        | Type              | Description |
| ----------- | ----------------- | ----------- |
| `$_manager` | `DatabaseManager` |             |

---

### open

```php
public static function open(string $server = 'self::DEFAULT_CONNECTION', bool $forceNew = false): DatabaseManager
```

Opens a connection to a database server, or returns the currently active connection to this server

Since `1.0`

#### Parameters

| Name        | Type     | Description                                                                                             |
| ----------- | -------- | ------------------------------------------------------------------------------------------------------- |
| `$server`   | `string` | Server configuration key (Defaults to __default).                                                       |
| `$forceNew` | `bool`   | If set, a new connection is open even if a previous similar one exists in the cache (Defaults to false) |

#### Returns

`DatabaseManager` 

#### Throws

| Exception                  | Reason                                                         |
| -------------------------- | -------------------------------------------------------------- |
| `DatabaseManagerException` | If no configuration is available nor valid for this server key |

---

