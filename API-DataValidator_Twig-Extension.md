# Extension Class

[`chsxf\MFX\DataValidator\Twig`](API-Namespace-DataValidator_Twig)

```php
class Extension extends Twig\Extension\AbstractExtension implements Twig\Extension\ExtensionInterface
```

## Summary

Data validator Twig extension class

Since `1.0`

## Methods

### getFieldValue

```php
public function getFieldValue(DataValidator $validator,  $fieldName)
```

Gets a field's value from a DataValidator

Since `1.0`

#### Parameters

| Name         | Type            | Description |
| ------------ | --------------- | ----------- |
| `$validator` | `DataValidator` |             |
| `$fieldName` | `string`        |             |

#### Returns

`mixed` 

---

### getIndexedFieldValue

```php
public function getIndexedFieldValue(DataValidator $validator,  $fieldName,  $index)
```

Gets a field's value at index from a DataValidator

Since `1.0`

#### Parameters

| Name         | Type            | Description |
| ------------ | --------------- | ----------- |
| `$validator` | `DataValidator` |             |
| `$fieldName` | `string`        |             |
| `$index`     | `int`           |             |

#### Returns

`mixed` 

---

