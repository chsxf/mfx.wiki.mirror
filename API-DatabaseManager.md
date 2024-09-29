# DatabaseManager Class

[`chsxf\MFX`](API-Namespace-chsxf_MFX)

```php
final class DatabaseManager implements Services\IDatabaseService
```

## Summary

Database manager class, acting as the default database service implementation

Since `1.0`

## Methods

### __construct

```php
public function __construct(Services\IConfigService $configService)
```

Constructor

Since `2.0`

#### Parameters

| Name             | Type             | Description |
| ---------------- | ---------------- | ----------- |
| `$configService` | `IConfigService` |             |

---

### close

```php
public function close(DatabaseConnectionInstance &$connectionInstance)
```

Closes a database server connection

Since `2.0`

#### Parameters

| Name                  | Type                         | Description                                 |
| --------------------- | ---------------------------- | ------------------------------------------- |
| `$connectionInstance` | `DatabaseConnectionInstance` | Reference to a database connection instance |

---

### open

```php
public function open(string $server = 'self::DEFAULT_CONNECTION', bool $forceNew = false): DatabaseConnectionInstance
```

Opens a connection to a database server, or returns the currently active instance to this server

Since `2.0`

#### Parameters

| Name        | Type     | Description                                                                                             |
| ----------- | -------- | ------------------------------------------------------------------------------------------------------- |
| `$server`   | `string` | Server configuration key (Defaults to __default).                                                       |
| `$forceNew` | `bool`   | If set, a new connection is open even if a previous similar one exists in the cache (Defaults to false) |

#### Returns

`DatabaseConnectionInstance` 

#### Throws

| Exception                  | Reason                                                         |
| -------------------------- | -------------------------------------------------------------- |
| `DatabaseManagerException` | If no configuration is available nor valid for this server key |

---

