# FieldTypeRegistry Class

[`chsxf\MFX\DataValidator`](API-Namespace-DataValidator)

```php
final class FieldTypeRegistry
```

## Summary

Since `1.0`

## Methods

### registerClassForType

```php
public static function registerClassForType(FieldType $type, string $className)
```

Registers a class name for a specific field type

Since `1.0`

#### Parameters

| Name         | Type        | Description |
| ------------ | ----------- | ----------- |
| `$type`      | `FieldType` | Field type  |
| `$className` | `string`    | Class name  |

#### Throws

| Exception                | Reason                                         |
| ------------------------ | ---------------------------------------------- |
| `DataValidatorException` | If a class is already registered for this type |

---

