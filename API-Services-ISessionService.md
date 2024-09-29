# ISessionService Interface

[`chsxf\MFX\Services`](API-Namespace-Services)

```php
interface ISessionService implements ArrayAccess
```

## Summary

Session service interface

Since `2.0`

## Methods

### setInSession

```php
public abstract function setInSession(array $values): void
```

Sets a set of values in the current session

Since `2.0`

#### Parameters

| Name      | Type    | Description                        |
| --------- | ------- | ---------------------------------- |
| `$values` | `array` | Associative array of values to set |

---

### unsetInSession

```php
public abstract function unsetInSession(string ...$keys): void
```

Unsets a set of values in the current session

Since `2.0`

#### Parameters

| Name    | Type       | Description                 |
| ------- | ---------- | --------------------------- |
| `$keys` | `string[]` | List of value keys to unset |

---

