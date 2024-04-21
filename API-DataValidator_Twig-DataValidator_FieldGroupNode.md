# DataValidator_FieldGroupNode Class

[`chsxf\MFX\DataValidator\Twig`](API-Namespace-DataValidator_Twig)

```php
class DataValidator_FieldGroupNode extends Twig\Node\Node implements Traversable, Stringable, IteratorAggregate, Countable
```

## Summary

Data validator field group Twig node

Since `1.0`

## Methods

### __construct

```php
public function __construct( $validatorName,  $groupName,  $nameIsString, Twig\Node\Node $body,  $line,  $tag)
```

Constructor

Since `1.0`

#### Parameters

| Name             | Type         | Description                                      |
| ---------------- | ------------ | ------------------------------------------------ |
| `$validatorName` | `string`     | Validator's name in Twig context                 |
| `$groupName`     | `string`     | Group's name                                     |
| `$nameIsString`  | `bool`       | If set, the group name is stored as a raw string |
| `$body`          | `\Twig_Node` | Body node                                        |
| `$line`          | `int`        | Line number of this node                         |
| `$tag`           | `string`     | Tag for this node                                |

---

