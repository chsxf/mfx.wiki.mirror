# ErrorManager Class

[`chsxf\MFX`](API-Namespace-chsxf_MFX)

```php
class ErrorManager
```

## Summary

Integrated error management class

Since `1.0`

## Properties

### $previousHandler

```php
public static $previousHandler = null;
```

---

## Methods

### flush

```php
public static function flush(?Twig\Environment $twig = null): string
```

Flushes error and notification messages for template display

Since `1.0`

#### Parameters

| Name    | Type                | Description                                                                                 |
| ------- | ------------------- | ------------------------------------------------------------------------------------------- |
| `$twig` | `\Twig_Environment` | Twig environment. If NULL, the function flushes containers only and returns an empty string |

#### Returns

`string` 

---

### flushToArray

```php
public static function flushToArray(array &$arr)
```

Flushes error and notification messages to an array

Since `1.0`

#### Parameters

| Name   | Type    | Description |
| ------ | ------- | ----------- |
| `$arr` | `array` |             |

---

### flushToArrayOrObject

```php
public static function flushToArrayOrObject(object|array &$arrOrObject)
```

Flushes error and notification messages to an array or an object

Since `1.0`

#### Parameters

| Name           | Type           | Description               |
| -------------- | -------------- | ------------------------- |
| `$arrOrObject` | `array|object` | Array or object to modify |

---

### flushToObject

```php
public static function flushToObject(object $object)
```

Flushes error and notification messages to an object

Since `1.0`

#### Parameters

| Name      | Type     | Description |
| --------- | -------- | ----------- |
| `$object` | `object` |             |

---

### freeze

```php
public static function freeze(bool $flush = false)
```

Freezes the error manager state into session data

Since `1.0`

#### Parameters

| Name     | Type   | Description                                           |
| -------- | ------ | ----------------------------------------------------- |
| `$flush` | `bool` | If set, flushes error containers. (Defaults to false) |

---

### hasError

```php
public static function hasError(): bool
```

Tells if the manager holds at least one error.

Since `1.0`

#### Returns

`boolean` 

---

### hasNotif

```php
public static function hasNotif(): bool
```

Tells if the manager holds at least one notification.

Since `1.0`

#### Returns

`boolean` 

---

### unfreeze

```php
public static function unfreeze()
```

Unfreezes the error manager state from session data if applying

Since `1.0`

---

