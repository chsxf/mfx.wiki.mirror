# User Class

[`chsxf\MFX`](API-Namespace-chsxf_MFX)

```php
class User
```

## Summary

User description class

Since `1.0`

## Methods

### __construct

```php
public function __construct(?string $key = null)
```

Constructor

Since `1.0`

#### Parameters

| Name   | Type     | Description |
| ------ | -------- | ----------- |
| `$key` | `string` | User key    |

---

### currentUser

```php
public static function currentUser(): ?User
```

Gets the current user reference

Since `1.0`

#### Returns

`User` 

---

### getKey

```php
public function getKey(): string
```

Gets the current user key

Since `1.0`

#### Returns

`string` The function returns NULL if no valid user is currently registered

---

### getKeyField

```php
public static function getKeyField(): string
```

Retrieves users management key field name

Since `1.0`

#### Returns

`string` 

#### Throws

| Exception                   | Reason                                                                                                                           |
| --------------------------- | -------------------------------------------------------------------------------------------------------------------------------- |
| `\InvalidArgumentException` | If the provided value is not a string or contains invalid characters (only underscores and alphanumeric characters are accepted) |

---

### getTableName

```php
public static function getTableName(): string
```

Retrieves users management table name

Since `1.0`

#### Returns

`string` 

#### Throws

| Exception                   | Reason                                                                                                                           |
| --------------------------- | -------------------------------------------------------------------------------------------------------------------------------- |
| `\InvalidArgumentException` | If the provided value is not a string or contains invalid characters (only underscores and alphanumeric characters are accepted) |

---

### invalidate

```php
public static function invalidate()
```

Invalidates user session.
Logs out the current valid user if existing

Since `1.0`

---

### isValid

```php
public function isValid(): bool
```

Gets the current user status.

Since `1.0`

#### Returns

`boolean` true if the current user is valid, false for guests

---

### registerFromKey

```php
public function registerFromKey( $key): bool
```

Register a user from its key

Since `1.0`

#### Parameters

| Name   | Type     | Description |
| ------ | -------- | ----------- |
| `$key` | `string` | User key    |

#### Returns

`boolean` true is the key is valid, false either

---

### registerWithFields

```php
public function registerWithFields(array $fields): bool
```

Register a user from database fields

Since `1.0`

#### Parameters

| Name      | Type    | Description                               |
| --------- | ------- | ----------------------------------------- |
| `$fields` | `array` | Database fields used to identify the user |

#### Returns

`boolean` true if the user is valid, false either

---

### validate

```php
public static function validate()
```

Validates user session

Since `1.0`

---

### validateWithFields

```php
public static function validateWithFields(array $fields): bool
```

Validates a user session using database fields

Since `1.0`

#### Parameters

| Name      | Type    | Description                             |
| --------- | ------- | --------------------------------------- |
| `$fields` | `array` | Key-value pairs for database validation |

#### Returns

`boolean` true if the session has been validated, false either

---

