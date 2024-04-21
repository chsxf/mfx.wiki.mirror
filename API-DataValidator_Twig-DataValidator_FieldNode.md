# DataValidator_FieldNode Class

[`chsxf\MFX\DataValidator\Twig`](API-Namespace-DataValidator_Twig)

```php
class DataValidator_FieldNode extends Twig\Node\Node implements Traversable, Stringable, IteratorAggregate, Countable
```

## Summary

Data validator field Twig node

Since `1.0`

## Methods

### __construct

```php
public function __construct( $validatorName,  $fieldName,  $id,  $idIsString,  $typeOverride,  $line,  $tag)
```

Constructor

Since `1.0`

#### Parameters

| Name             | Type     | Description                                                                 |
| ---------------- | -------- | --------------------------------------------------------------------------- |
| `$validatorName` | `string` | Validator's name in Twig context                                            |
| `$fieldName`     | `string` | Field's name                                                                |
| `$id`            | `string` | Field's ID for the HTML output                                              |
| `$idIsString`    | `bool`   | If set, the field's ID is stored as a raw string                            |
| `$typeOverride`  | `string` | Field type to use to override the initial field type. If NULL, no override. |
| `$line`          | `int`    | Line number of this node                                                    |
| `$tag`           | `string` | Tag for this node                                                           |

---

