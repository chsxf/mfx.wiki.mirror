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
public function __construct(Services\IAuthenticationService $authenticationService, Services\IDatabaseService $databaseService)
```

Constructor

Since `2.0`

#### Parameters

| Name                     | Type                     | Description                     |
| ------------------------ | ------------------------ | ------------------------------- |
| `$authenticationService` | `IAuthenticationService` | Authentication service instance |
| `$databaseService`       | `IDatabaseService`       | Database service instance       |

---

### getId

```php
public function getId(): string|int|null
```

Gets the current user identifier

Since `2.0`

#### Returns

`string|int|null` The function returns NULL if no valid user is currently registered

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

### validateWithFields

```php
public function validateWithFields(array $fields): bool
```

Validates a user from database fields

Since `2.0`

#### Parameters

| Name      | Type    | Description                               |
| --------- | ------- | ----------------------------------------- |
| `$fields` | `array` | Database fields used to identify the user |

#### Returns

`boolean` true if the user is valid, false either

---

### validateWithId

```php
public function validateWithId(string|int|null $id): bool
```

Validates the user from its identifier

Since `2.0`

#### Parameters

| Name  | Type              | Description                 |
| ----- | ----------------- | --------------------------- |
| `$id` | `string|int|null` | User identifier to validate |

#### Returns

`boolean` true if the user identifier is valid, false either

---

