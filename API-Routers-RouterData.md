# RouterData Class

[`chsxf\MFX\Routers`](API-Namespace-Routers)

```php
final class RouterData
```

## Summary

Since `1.0`

## Properties

### $defaultTemplate

```php
public readonly string $defaultTemplate ;
```

---

### $route

```php
public readonly string $route ;
```

---

### $routeAttributes

```php
public readonly Attributes\RouteAttributesParser $routeAttributes ;
```

---

### $routeMethod

```php
public readonly ReflectionMethod $routeMethod ;
```

---

### $routeParams

```php
public readonly array $routeParams ;
```

---

### $routeProviderAttributes

```php
public readonly Attributes\RouteAttributesParser $routeProviderAttributes ;
```

---

## Methods

### __construct

```php
public function __construct(string $route, Attributes\RouteAttributesParser $routeProviderAttributes, Attributes\RouteAttributesParser $routeAttributes, array $routeParams, ReflectionMethod $routeMethod, string $defaultTemplate)
```

Since `1.0`

#### Parameters

| Name                       | Type                    | Description |
| -------------------------- | ----------------------- | ----------- |
| `$route`                   | `string`                |             |
| `$routeProviderAttributes` | `RouteAttributesParser` |             |
| `$routeAttributes`         | `RouteAttributesParser` |             |
| `$routeParams`             | `array`                 |             |
| `$routeMethod`             | `ReflectionMethod`      |             |
| `$defaultTemplate`         | `string`                |             |

---

