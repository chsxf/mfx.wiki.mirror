# InIntRange Class

[`chsxf\MFX\DataValidator\Filters`](API-Namespace-DataValidator_Filters)

```php
class InIntRange extends chsxf\MFX\DataValidator\AbstractFilter
```

## Summary

Descriptor of a filter field checking presence of the value in a Min Max range

Since `1.0`

## Methods

### __construct

```php
public function __construct(int $value1, int $value2, bool $includeMax = false, ?string $message = null)
```

Constructor

Since `1.0`

#### Parameters

| Name          | Type     | Description                                                                     |
| ------------- | -------- | ------------------------------------------------------------------------------- |
| `$min`        | `int`    | the minimum value                                                               |
| `$max`        | `int`    | the maximum value                                                               |
| `$includeMax` | `bool`   | If set, includes the max value. If not, the max value is not part of the range. |
| `$message`    | `string` | Error message                                                                   |

---

