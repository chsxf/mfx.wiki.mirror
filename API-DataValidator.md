# DataValidator Class

[`chsxf\MFX`](API-Namespace-chsxf_MFX)

```php
final class DataValidator implements ArrayAccess
```

## Summary

Data validator class

Instances of this class are used as a entry point for data validation procedures.

Since `1.0`

## Methods

### __construct

```php
public function __construct(?array $fields = null)
```

Constructor

Since `1.0`

#### Parameters

| Name      | Type    | Description                          |
| --------- | ------- | ------------------------------------ |
| `$fields` | `array` | Pre-allocated data validation fields |

---

### addField

```php
public function addField(DataValidator\Field $field): DataValidator\Field
```

Adds a field to the data validator

Since `1.0`

#### Parameters

| Name     | Type                                             | Description |
| -------- | ------------------------------------------------ | ----------- |
| `$field` | [`DataValidator\Field`](API-DataValidator-Field) |             |

#### Returns

[`DataValidator\Field`](API-DataValidator-Field) The added field

#### Throws

| Exception                                                                          | Reason                                       |
| ---------------------------------------------------------------------------------- | -------------------------------------------- |
| [`DataValidator\DataValidatorException`](API-DataValidator-DataValidatorException) | If a field with the same name already exists |

---

### createField

```php
public function createField(string $name, DataValidator\FieldType $type, mixed $defaultValue = null, bool $required = true, array $extras = array()): DataValidator\Field
```

Creates and add a field to the data validator

See `Field::addField()`

Since `1.0`

#### Parameters

| Name            | Type                                                     | Description                                            |
| --------------- | -------------------------------------------------------- | ------------------------------------------------------ |
| `$name`         | `string`                                                 | Field's name                                           |
| `$type`         | [`DataValidator\FieldType`](API-DataValidator-FieldType) | Field's type                                           |
| `$defaultValue` | `mixed`                                                  | Field's default value (Defaults to NULL)               |
| `$required`     | `boolean`                                                | If set, the field will be required. (Defaults to true) |
| `$extras`       | `array`                                                  | Extra options                                          |

#### Returns

[`DataValidator\Field`](API-DataValidator-Field) 

---

### generate

```php
public function generate(string $name, ?DataValidator\FieldType $typeOverride = null)
```

Generates the HTML representation of a field

Since `1.0`

#### Parameters

| Name            | Type                                                     | Description                                                                           |
| --------------- | -------------------------------------------------------- | ------------------------------------------------------------------------------------- |
| `$name`         | `string`                                                 | Field's name to generate                                                              |
| `$typeOverride` | [`DataValidator\FieldType`](API-DataValidator-FieldType) | Type to use to override original field type. If NULL, no override. (Defaults to NULL) |

#### Throws

| Exception                                                                          | Reason                            |
| ---------------------------------------------------------------------------------- | --------------------------------- |
| [`DataValidator\DataValidatorException`](API-DataValidator-DataValidatorException) | If no field exists with this name |

---

### getFieldValue

```php
public function getFieldValue(string $name, bool $returnDefaultIfNotSet = false, bool $makeEmptyStringsNull = false): mixed
```

Gets the value of a field

Since `1.0`

#### Parameters

| Name                     | Type      | Description                                                                                      |
| ------------------------ | --------- | ------------------------------------------------------------------------------------------------ |
| `$name`                  | `string`  | Field name                                                                                       |
| `$returnDefaultIfNotSet` | `boolean` | If set, the default value of the field is returned is none has been provided (Defaults to false) |
| `$makeEmptyStringsNull`  | `boolean` | If set, all empty string values will be set to NULL. (Defaults to false)                         |

#### Throws

| Exception                                                                          | Reason                            |
| ---------------------------------------------------------------------------------- | --------------------------------- |
| [`DataValidator\DataValidatorException`](API-DataValidator-DataValidatorException) | If no field exists with this name |

---

### getFieldValues

```php
public function getFieldValues(string $prefix = '', array $excludes = array(), bool $returnDefaultIfNotSet = false, bool $makeEmptyStringsNull = false): array
```

Gets values for all fields

Since `1.0`

#### Parameters

| Name                     | Type      | Description                                                                                      |
| ------------------------ | --------- | ------------------------------------------------------------------------------------------------ |
| `$prefix`                | `string`  | Prefix to use for all field name in the resulting array (Defaults to no prefix)                  |
| `$excludes`              | `array`   | List of fields to exclude from the resulting array (Defaults to an empty array)                  |
| `$returnDefaultIfNotSet` | `string`  | If set, the default value of the field is returned if none has been provided (Defaults to false) |
| `$makeEmptyStringsNull`  | `boolean` | If set, all empty string values will be set to NULL. (Defaults to false)                         |

#### Returns

`array` 

---

### getIndexedFieldValue

```php
public function getIndexedFieldValue(string $name, int $index, bool $returnDefaultIfNotSet = false, bool $makeEmptyStringsNull = false): mixed
```

Gets the value of a field

Since `1.0`

#### Parameters

| Name                     | Type      | Description                                                                                      |
| ------------------------ | --------- | ------------------------------------------------------------------------------------------------ |
| `$name`                  | `string`  | Field name                                                                                       |
| `$index`                 | `int`     | Index of the value to retrieve                                                                   |
| `$returnDefaultIfNotSet` | `boolean` | If set, the default value of the field is returned is none has been provided (Defaults to false) |
| `$makeEmptyStringsNull`  | `boolean` | If set, all empty string values will be set to NULL. (Defaults to false)                         |

#### Throws

| Exception                                                                          | Reason                            |
| ---------------------------------------------------------------------------------- | --------------------------------- |
| [`DataValidator\DataValidatorException`](API-DataValidator-DataValidatorException) | If no field exists with this name |

---

### getIndexedFieldValues

```php
public function getIndexedFieldValues(int $index, string $prefix = '', array $excludes = array(), bool $returnDefaultIfNotSet = false, bool $makeEmptyStringsNull = false): array
```

Gets indexed values for all fields

Since `1.0`

#### Parameters

| Name                     | Type      | Description                                                                                      |
| ------------------------ | --------- | ------------------------------------------------------------------------------------------------ |
| `$index`                 | `int`     | Index of the values in fields                                                                    |
| `$name`                  | `string`  | Field name                                                                                       |
| `$prefix`                | `string`  | Prefix to use for all field name in the resulting array (Defaults to no prefix)                  |
| `$excludes`              | `array`   | List of fields to exclude from the resulting array (Defaults to an empty array)                  |
| `$returnDefaultIfNotSet` | `string`  | If set, the default value of the field is returned if none has been provided (Defaults to false) |
| `$makeEmptyStringsNull`  | `boolean` | If set, all empty string values will be set to NULL. (Defaults to false)                         |

#### Returns

`array` 

---

### popGenerationGroup

```php
public function popGenerationGroup()
```

Pops a generation group name

Since `1.0`

---

### pushGenerationGroup

```php
public function pushGenerationGroup(string $name)
```

Pushes a generation group name

Since `1.0`

#### Parameters

| Name    | Type     | Description |
| ------- | -------- | ----------- |
| `$name` | `string` |             |

---

### resetRepeatCounters

```php
public function resetRepeatCounters()
```

Resets the repeat counters for all fields

Since `1.0`

---

### validate

```php
public function validate(Traversable|array $data, bool $silent = false): bool
```

Validates data based on field descriptors

Since `1.0`

#### Parameters

| Name      | Type                 | Description                                       |
| --------- | -------------------- | ------------------------------------------------- |
| `$data`   | `array|\Traversable` | Data to validate                                  |
| `$silent` | `boolean`            | If set, no error is triggered (defaults to false) |

#### Returns

`boolean` true if data is valid, false either

---

