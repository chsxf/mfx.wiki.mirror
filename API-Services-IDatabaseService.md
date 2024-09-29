# IDatabaseService Interface

[`chsxf\MFX\Services`](API-Namespace-Services)

```php
interface IDatabaseService
```

## Summary

Database service interface

Since `2.0`

## Constants

```php
public const DEFAULT_CONNECTION = '__default';
```

Default connection name constant

Since `2.0`

## Methods

### close

```php
public abstract function close(DatabaseConnectionInstance &$connectionInstance)
```

Attempts to close a connection instance.
The connection instance variable is passed as a reference and will be null after the call to this function.
Please note that the connection will only be closed after all references to it have been released.
You're responsible for cleaning your own additional references if existing.

Since `2.0`

#### Parameters

| Name                  | Type                         | Description |
| --------------------- | ---------------------------- | ----------- |
| `$connectionInstance` | `DatabaseConnectionInstance` |             |

---

### open

```php
public abstract function open(string $server = 'self::DEFAULT_CONNECTION', bool $forceNew = false): DatabaseConnectionInstance
```

Opens a connection to a database server, or returns the currently active connection to this server

Since `2.0`

#### Parameters

| Name        | Type     | Description                                                                                             |
| ----------- | -------- | ------------------------------------------------------------------------------------------------------- |
| `$server`   | `string` | Server configuration key (Defaults to __default).                                                       |
| `$forceNew` | `bool`   | If set, a new connection is open even if a previous similar one exists in the cache (Defaults to false) |

#### Returns

`DatabaseConnectionInstance` 

---

