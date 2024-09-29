# UserManager Class

[`chsxf\MFX`](API-Namespace-chsxf_MFX)

```php
final class UserManager implements Services\IAuthenticationService
```

## Summary

User management class

Since `2.0`

## Methods

### __construct

```php
public function __construct(Services\IConfigService $configService, Services\IDatabaseService $databaseService, Services\ISessionService $sessionService)
```

Constructor

Since `2.0`

#### Parameters

| Name               | Type               | Description               |
| ------------------ | ------------------ | ------------------------- |
| `$configService`   | `IConfigService`   | Config service instance   |
| `$databaseService` | `IDatabaseService` | Database service instance |
| `$sessionService`  | `ISessionService`  | Session service instance  |

---

### getCurrentAuthenticatedUser

```php
public function getCurrentAuthenticatedUser(): ?User
```

Gets the current user reference

Since `2.0`

#### Returns

`User` 

---

### getIdField

```php
public function getIdField(): string
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
public function getTableName(): string
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
public function hasAuthenticatedUser(): bool
```

Tells if an authenticated user currently exists

Since `2.0`

#### Returns

`bool` 

---

### invalidate

```php
public function invalidate()
```

Invalidates user session.
Logs out the current valid user if existing

Since `2.0`

---

### isEnabled

```php
public function isEnabled(): bool
```

Tells if user management is enabled

Since `2.0`

#### Returns

`bool` 

---

### validateWithFields

```php
public function validateWithFields(array $fields): bool
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

