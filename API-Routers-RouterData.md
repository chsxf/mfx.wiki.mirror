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
public readonly RouteAttributesParser $routeAttributes ;
```

---

### $routeParams

```php
public readonly array $routeParams ;
```

---

### $routeProviderAttributes

```php
public readonly RouteAttributesParser $routeProviderAttributes ;
```

---

## Methods

### create

```php
public static function create(Services\ICoreServiceProvider $coreServiceProvider, string $route, array $routeParams, string $providerClassName, string $routeMethodName): RouterData
```

Create a new RouterData instance

Since `2.0`

#### Parameters

| Name                   | Type                   | Description                    |
| ---------------------- | ---------------------- | ------------------------------ |
| `$coreServiceProvider` | `ICoreServiceProvider` | Core service provider instance |
| `$route`               | `string`               | Parsed route name              |
| `$routeParams`         | `array`                | Route parameters               |
| `$providerClassName`   | `string`               | Route provider class name      |
| `$routeMethodName`     | `string`               | Route method to invoke         |

#### Returns

`RouterData` 

#### Throws

| Exception             | Reason |
| --------------------- | ------ |
| `MFXException`        |        |
| `ReflectionException` |        |

---

### getResult

```php
public function getResult(): RequestResult
```

Since `1.0`

---

