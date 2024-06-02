# PathRouter Class

[`chsxf\MFX\Routers`](API-Namespace-Routers)

```php
class PathRouter implements IRouter
```

## Summary

Since `1.0`

## Methods

### parseRoute

```php
public function parseRoute(string $filteredPathInfo, string $defaultRoute): RouterData
```

Since `1.0`

#### Parameters

| Name                | Type     | Description |
| ------------------- | -------- | ----------- |
| `$filteredPathInfo` | `string` |             |
| `$defaultRoute`     | `string` |             |

#### Returns

`RouterData` 

#### Throws

| Exception             | Reason |
| --------------------- | ------ |
| `ErrorException`      |        |
| `ReflectionException` |        |

---

