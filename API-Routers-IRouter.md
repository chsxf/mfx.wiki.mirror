# IRouter Interface

[`chsxf\MFX\Routers`](API-Namespace-Routers)

```php
interface IRouter
```

## Summary

Interface routers must implement

Since `1.0`

## Methods

### parseRoute

```php
public abstract function parseRoute(Services\ICoreServiceProvider $coreServiceProvider, string $filteredPathInfo, string $defaultRoute): RouterData
```

Parses route data from the provided information

Since `Z.0`

#### Parameters

| Name                   | Type                   | Description                           |
| ---------------------- | ---------------------- | ------------------------------------- |
| `$coreServiceProvider` | `ICoreServiceProvider` | Core service provider instance        |
| `$filteredPathInfo`    | `string`               | Path info for the request             |
| `$defaultRoute`        | `string`               | Default route to use if none provided |

#### Returns

`RouterData` 

---

