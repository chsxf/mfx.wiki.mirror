# SessionManager Class

[`chsxf\MFX`](API-Namespace-chsxf_MFX)

```php
final class SessionManager implements Services\ISessionService, ArrayAccess
```

## Summary

Session management class

Since `2.0`

## Methods

### __construct

```php
public function __construct(Services\IConfigService $configService)
```

Constructor

Since `2.0`

#### Parameters

| Name             | Type             | Description             |
| ---------------- | ---------------- | ----------------------- |
| `$configService` | `IConfigService` | Config service instance |

#### Throws

| Exception      | Reason |
| -------------- | ------ |
| `MFXException` |        |

---

### setInSession

```php
public function setInSession(array $values): void
```

Set multiple values in session at once

Since `2.0`

#### Parameters

| Name      | Type    | Description                    |
| --------- | ------- | ------------------------------ |
| `$values` | `array` | Values as an associative array |

---

### unsetInSession

```php
public function unsetInSession(string ...$keys): void
```

Unsets multiple values in session at once

Since `2.0`

#### Parameters

| Name    | Type    | Description                             |
| ------- | ------- | --------------------------------------- |
| `$keys` | `array` | List of session variable names to unset |

---

