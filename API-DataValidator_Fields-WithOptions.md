# WithOptions Class

[`chsxf\MFX\DataValidator\Fields`](API-Namespace-DataValidator_Fields)

```php
class WithOptions extends chsxf\MFX\DataValidator\Field
```

## Summary

Descriptor of a field type with multiple options (such as 'select' or 'radio' types)

Since `1.0`

## Methods

### addOption

```php
public function addOption(string $label, ?string $value = null, ?string $group = null)
```

Add an option to the list

Since `1.0`

#### Parameters

| Name     | Type     | Description                                                                                   |
| -------- | -------- | --------------------------------------------------------------------------------------------- |
| `$label` | `string` | Option label                                                                                  |
| `$value` | `string` | Option value. Equals to label if NULL. (Defaults to NULL)                                     |
| `$group` | `string` | Option group. If set, the option will be added to the corresponding group. (Defaults to NULL) |

---

### addOptions

```php
public function addOptions(array $options, bool $useAsKeyValueStore = false, ?string $group = null)
```

Add options to the list

Since `1.0`

#### Parameters

| Name                  | Type     | Description                                                                                                                                                                             |
| --------------------- | -------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `$options`            | `array`  | Options array. Items may be mixed scalar values and arrays. If an item is an array, it should have keys 'value' and 'label'.                                                            |
| `$useAsKeyValueStore` | `bool`   | If set, items for the $options array that are not arrays themselves will be considered as key/value pairs. If not set, item value will be used for label and value. (Defaults to false) |
| `$group`              | `string` | Options group. If set, the options will be added to the corresponding group. (Defaults to NULL)                                                                                         |

---

