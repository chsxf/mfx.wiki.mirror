# MatchFilter Class

[`chsxf\MFX\DataValidator\Filters`](API-Namespace-DataValidator_Filters)

```php
class MatchFilter extends chsxf\MFX\DataValidator\AbstractOtherFieldFilter
```

## Summary

Description of a filter validating when the field's matched another field's one

Since `1.0`

## Methods

### __construct

```php
public function __construct(DataValidator\Field|array $otherFields, ?string $message = null)
```

Constructor

Since `1.0`

#### Parameters

| Name           | Type          | Description                                   |
| -------------- | ------------- | --------------------------------------------- |
| `$otherFields` | `Field|array` | One or more references to the matching fields |
| `$message`     | `string`      | Error message                                 |

---

