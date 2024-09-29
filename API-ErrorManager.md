# ErrorManager Class

[`chsxf\MFX`](API-Namespace-chsxf_MFX)

```php
final class ErrorManager
```

## Summary

Integrated error management class

Since `1.0`

## Methods

### __construct

```php
public function __construct(Services\IConfigService $configService, Services\ISessionService $sessionService)
```

Constructor

Since `2.0`

#### Parameters

| Name              | Type              | Description              |
| ----------------- | ----------------- | ------------------------ |
| `$configService`  | `IConfigService`  | Config service instance  |
| `$sessionService` | `ISessionService` | Session service instance |

#### Throws

| Exception      | Reason |
| -------------- | ------ |
| `MFXException` |        |

---

### flush

```php
public function flush(?Twig\Environment $twig = null): string
```

Flushes error and notification messages for template display

Since `2.0`

#### Parameters

| Name    | Type                | Description                                                                                 |
| ------- | ------------------- | ------------------------------------------------------------------------------------------- |
| `$twig` | `\Twig_Environment` | Twig environment. If NULL, the function flushes containers only and returns an empty string |

#### Returns

`string` 

---

### flushToArrayOrObject

```php
public function flushToArrayOrObject(object|array &$arrOrObject)
```

Flushes error and notification messages to an array or an object

Since `2.0`

#### Parameters

| Name           | Type           | Description               |
| -------------- | -------------- | ------------------------- |
| `$arrOrObject` | `array|object` | Array or object to modify |

---

### freeze

```php
public function freeze(bool $flush = false)
```

Freezes the error manager state into session data

Since `2.0`

#### Parameters

| Name     | Type   | Description                                           |
| -------- | ------ | ----------------------------------------------------- |
| `$flush` | `bool` | If set, flushes error containers. (Defaults to false) |

---

### hasError

```php
public function hasError(): bool
```

Tells if the manager holds at least one error.

Since `2.0`

#### Returns

`boolean` 

---

### hasNotif

```php
public function hasNotif(): bool
```

Tells if the manager holds at least one notification.

Since `2.0`

#### Returns

`boolean` 

---

