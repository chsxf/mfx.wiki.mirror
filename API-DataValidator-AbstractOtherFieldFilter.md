# AbstractOtherFieldFilter Class

[`chsxf\MFX\DataValidator`](API-Namespace-DataValidator)

```php
abstract class AbstractOtherFieldFilter extends AbstractFilter
```

## Summary

Description of a filter validating if the field matches another one

Since `1.0`

## Methods

### __construct

```php
public function __construct(Field|array $otherFields, ?string $message = null)
```

Constructor

Since `1.0`

#### Parameters

| Name           | Type          | Description                                   |
| -------------- | ------------- | --------------------------------------------- |
| `$otherFields` | `Field|array` | One or more references to the matching fields |
| `$message`     | `string`      | Error message                                 |

---

