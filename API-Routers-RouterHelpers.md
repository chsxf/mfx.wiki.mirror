# RouterHelpers Class

[`chsxf\MFX\Routers`](API-Namespace-Routers)

```php
final class RouterHelpers
```

## Summary

Since `1.0`

## Methods

### check404file

```php
public static function check404file(array $routeParams)
```

Checks if the request could be referring to a missing file and replies a 404 HTTP error code

Since `1.0`

#### Parameters

| Name           | Type    | Description              |
| -------------- | ------- | ------------------------ |
| `$routeParams` | `array` | Request route parameters |

---

### getRouteProviderClass

```php
public static function getRouteProviderClass(string $providerClassName): ?ReflectionClass
```

---

### isMethodValidRoute

```php
public static function isMethodValidRoute(ReflectionMethod $method): Attributes\RouteAttributesParser|false
```

Checks if a specific method is a valid route

Since `1.0`

#### Parameters

| Name      | Type                | Description       |
| --------- | ------------------- | ----------------- |
| `$method` | `\ReflectionMethod` | Method to inspect |

#### Returns

`RouteAttributesParser|false` The route's attributes parser or false in case of an error

---

