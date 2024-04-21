# AbstractFilter Class

[`chsxf\MFX\DataValidator`](API-Namespace-DataValidator)

```php
abstract class AbstractFilter
```

## Summary

Abstract data validation filter class

All filters must inherit from this class.

Since `1.0`

## Methods

### __construct

```php
public function __construct(?string $message = null)
```

Constructor

Since `1.0`

#### Parameters

| Name       | Type     | Description   |
| ---------- | -------- | ------------- |
| `$message` | `string` | Error message |

---

### appliesToField

```php
public function appliesToField(): bool
```

Tells if this filter must be applied to the field's values or to the field instance only

Since `1.0`

#### Returns

`boolean` 

---

### mayBeSkipped

```php
public function mayBeSkipped(int $atIndex = -1): bool
```

Tells if this filter can be skipped during the validation process if the field is not required and has no value.

Since `1.0`

#### Parameters

| Name       | Type  | Description                                                                |
| ---------- | ----- | -------------------------------------------------------------------------- |
| `$atIndex` | `int` | Index for repeatable fields. If -1, no index is provided. (Defaults to -1) |

#### Returns

`boolean` 

---

### setMessageDispatcher

```php
public final function setMessageDispatcher(IMessageDispatcher $dispatcher)
```

Overriddes the default message dispatcher

Since `1.0`

#### Parameters

| Name          | Type                                                         | Description |
| ------------- | ------------------------------------------------------------ | ----------- |
| `$dispatcher` | [`IMessageDispatcher`](API-DataValidator-IMessageDispatcher) |             |

---

### validate

```php
public abstract function validate(string $fieldName, mixed $value, int $atIndex = -1, bool $silent = false): bool
```

Validates value

Since `1.0`

#### Parameters

| Name         | Type      | Description                                                                |
| ------------ | --------- | -------------------------------------------------------------------------- |
| `$fieldName` | `string`  | Field name                                                                 |
| `$value`     | `mixed`   | Value to validate                                                          |
| `$atIndex`   | `int`     | Index for repeatable fields. If -1, no index is provided. (Defaults to -1) |
| `$silent`    | `boolean` | If set, no error is triggered (defaults to false)                          |

#### Returns

`bool` true if the filter validates, false either

---

