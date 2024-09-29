# RouteAttributesParser Class

[`chsxf\MFX\Routers`](API-Namespace-Routers)

```php
class RouteAttributesParser
```

## Summary

Since `1.0`

## Methods

### __construct

```php
public function __construct(ReflectionClass|ReflectionMethod $reflectedElement)
```

Since `1.0`

#### Parameters

| Name                | Type                               | Description |
| ------------------- | ---------------------------------- | ----------- |
| `$reflectedElement` | `ReflectionClass|ReflectionMethod` |             |

---

### getAttributeValue

```php
public function getAttributeValue(string $class, ?string $defaultValue = null): ?string
```

Since `1.0`

#### Parameters

| Name            | Type          | Description |
| --------------- | ------------- | ----------- |
| `$class`        | `string`      |             |
| `$defaultValue` | `null|string` |             |

#### Returns

`null|string` 

#### Throws

| Exception                | Reason |
| ------------------------ | ------ |
| `DataValidatorException` |        |

---

### hasAttribute

```php
public function hasAttribute(string $class)
```

Since `1.0`

#### Parameters

| Name     | Type     | Description |
| -------- | -------- | ----------- |
| `$class` | `string` |             |

#### Returns

`bool` 

---

