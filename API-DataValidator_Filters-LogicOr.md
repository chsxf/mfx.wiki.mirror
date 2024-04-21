# LogicOr Class

[`chsxf\MFX\DataValidator\Filters`](API-Namespace-DataValidator_Filters)

```php
class LogicOr extends chsxf\MFX\DataValidator\AbstractFilter implements DataValidator\IMessageDispatcher
```

## Summary

Descriptor of a field filter applying a basic "OR" logic operation on other filters

This filter validates as soon as a contained filter validates.

Since `1.0`

## Methods

### __construct

```php
public function __construct()
```

Constructor

Since `1.0`

---

### addFilter

```php
public function addFilter(DataValidator\AbstractFilter $filter)
```

Adds a filter

Since `1.0`

#### Parameters

| Name      | Type             | Description |
| --------- | ---------------- | ----------- |
| `$filter` | `AbstractFilter` |             |

---

