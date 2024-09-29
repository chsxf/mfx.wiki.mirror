# IAuthenticationService Interface

[`chsxf\MFX\Services`](API-Namespace-Services)

```php
interface IAuthenticationService
```

## Summary

Authentication service interface

Since `2.0`

## Methods

### getCurrentAuthenticatedUser

```php
public abstract function getCurrentAuthenticatedUser(): ?User
```

Gets the current user reference, if an authenticated user exists

Since `2.0`

#### Returns

`User` 

---

### getIdField

```php
public abstract function getIdField(): string
```

Retrieves users management identifier field name

Since `2.0`

#### Returns

`string` 

#### Throws

| Exception      | Reason                                                                                                                           |
| -------------- | -------------------------------------------------------------------------------------------------------------------------------- |
| `MFXException` | If the provided value is not a string or contains invalid characters (only underscores and alphanumeric characters are accepted) |

---

### getTableName

```php
public abstract function getTableName(): string
```

Retrieves users management table name

Since `2.0`

#### Returns

`string` 

#### Throws

| Exception      | Reason                                                                                                                           |
| -------------- | -------------------------------------------------------------------------------------------------------------------------------- |
| `MFXException` | If the provided value is not a string or contains invalid characters (only underscores and alphanumeric characters are accepted) |

---

### hasAuthenticatedUser

```php
public abstract function hasAuthenticatedUser(): bool
```

Tells if an authenticated user currently exists

Since `2.0`

#### Returns

`bool` 

---

### invalidate

```php
public abstract function invalidate()
```

Invalidates user session.
Logs out the current authenticated user if existing

Since `2.0`

---

### isEnabled

```php
public abstract function isEnabled(): bool
```

Tells if user management is enabled

Since `2.0`

#### Returns

`bool` 

---

### validateWithFields

```php
public abstract function validateWithFields(array $fields): bool
```

Validates a user session using database fields

Since `2.0`

#### Parameters

| Name      | Type    | Description                             |
| --------- | ------- | --------------------------------------- |
| `$fields` | `array` | Key-value pairs for database validation |

#### Returns

`boolean` true if the session has been validated, false either

---

