# Field Class

[`chsxf\MFX\DataValidator`](API-Namespace-DataValidator)

```php
class Field
```

## Summary

Descriptor of a data validator field

Since `1.0`

## Methods

### addExtra

```php
public final function addExtra(string $key, string $value)
```

Adds extra option to field

Since `1.0`

#### Parameters

| Name     | Type     | Description  |
| -------- | -------- | ------------ |
| `$name`  | `string` | Option name  |
| `$value` | `string` | Option value |

---

### addExtras

```php
public final function addExtras(array $extras)
```

Adds extra options to field

Since `1.0`

#### Parameters

| Name      | Type    | Description                                                                |
| --------- | ------- | -------------------------------------------------------------------------- |
| `$extras` | `array` | Associative array whose keys are option names and values are option values |

---

### addFilter

```php
public final function addFilter(AbstractFilter $filter)
```

Adds a validation filter to this field

Since `1.0`

#### Parameters

| Name      | Type             | Description |
| --------- | ---------------- | ----------- |
| `$filter` | `AbstractFilter` |             |

---

### create

```php
public static function create(string $name, FieldType $type, mixed $defaultValue = null, bool $required = true): Field
```

Helper function to create fields

Since `1.0`

#### Parameters

| Name            | Type        | Description                                            |
| --------------- | ----------- | ------------------------------------------------------ |
| `$name`         | `string`    | Field's name                                           |
| `$type`         | `FieldType` | Field's type                                           |
| `$defaultValue` | `mixed`     | Field's default value (Defaults to NULL)               |
| `$required`     | `boolean`   | If set, the field will be required. (Defaults to true) |

#### Returns

`Field` 

---

### generate

```php
public function generate(array $containingGroups = array(), ?FieldType $typeOverride = null): array
```

Generates the HTML representation of this field

Since `1.0`

#### Parameters

| Name                | Type        | Description                                                                           |
| ------------------- | ----------- | ------------------------------------------------------------------------------------- |
| `$containingGroups` | `array`     | Containing groups                                                                     |
| `$typeOverride`     | `FieldType` | Type to use to override original field type. If NULL, no override. (Defaults to NULL) |

#### Returns

`array` 

---

### getDefaultValue

```php
public function getDefaultValue(): mixed
```

Get this field's default value

Since `1.0`

#### Returns

`mixed` 

---

### getHTMLType

```php
public function getHTMLType(?FieldType $typeOverride = null): string
```

Gets the HTML type of this field

Since `1.0`

#### Parameters

| Name            | Type        | Description                                                                           |
| --------------- | ----------- | ------------------------------------------------------------------------------------- |
| `$typeOverride` | `FieldType` | Type to use to override original field type. If NULL, no override. (Defaults to NULL) |

#### Returns

`string` 

---

### getIndexedValue

```php
public function getIndexedValue(int $index, bool $returnDefaultIfNotSet = false): mixed
```

Get a indexed value from this field if repeatable

Since `1.0`

#### Parameters

| Name                     | Type   | Description                                                                             |
| ------------------------ | ------ | --------------------------------------------------------------------------------------- |
| `$index`                 | `int`  | Index of the value to retrieve                                                          |
| `$returnDefaultIfNotSet` | `bool` | If set, the function returns the default value if the field has not been populated yet. |

#### Returns

`mixed` the indexed value or the field's value if the field is not repeatable.

---

### getMaxRepeatIndex

```php
public final function getMaxRepeatIndex(): int
```

Retrieves the maximal defined repeat index for a repeatable field.

Since `1.0`

#### Returns

`number` -1 if no maximal index can be guessed or the actual value

---

### getName

```php
public function getName(): string
```

Gets the name of this field

Since `1.0`

#### Returns

`string` 

---

### getType

```php
public function getType(): FieldType
```

Gets the type of this field

Since `1.0`

#### Returns

`FieldType` 

---

### getValue

```php
public function getValue(bool $returnDefaultIfNotSet = false): mixed
```

Gets this field's value

Since `1.0`

#### Parameters

| Name                     | Type      | Description                                                                             |
| ------------------------ | --------- | --------------------------------------------------------------------------------------- |
| `$returnDefaultIfNotSet` | `boolean` | If set, the function returns the default value if the field has not been populated yet. |

#### Returns

`mixed` 

---

### hasDefaultValue

```php
public function hasDefaultValue(): bool
```

Tells if this field as a default value or not

Since `1.0`

#### Returns

`boolean` 

---

### isEnabled

```php
public final function isEnabled(): bool
```

Tells if the field is enabled

Since `1.0`

#### Returns

`boolean` 

---

### isReadOnly

```php
public final function isReadOnly(): bool
```

Tells if the field is read only

Since `1.0`

#### Returns

`boolean` 

---

### isRepeatable

```php
public final function isRepeatable(): bool
```

Tells if this field is repeatable

Since `1.0`

#### Returns

`boolean` 

---

### isRequired

```php
public function isRequired(): bool
```

Tells if this field is required or not

Since `1.0`

#### Returns

`boolean` 

---

### removeFilter

```php
public final function removeFilter(AbstractFilter $filter)
```

Removes a validation filter from this field

Since `1.0`

#### Parameters

| Name      | Type             | Description |
| --------- | ---------------- | ----------- |
| `$filter` | `AbstractFilter` |             |

---

### repeatableUpTo

```php
public final function repeatableUpTo(): int
```

Tells the maximum number of iterations for this repeatable field

Since `1.0`

#### Returns

`int` The maximum number of iterations or -1 if no limit.

---

### resetRepeatCounter

```php
public final function resetRepeatCounter()
```

Resets this field's repeat counter

Since `1.0`

---

### revertToDefaultIfNotPopulated

```php
public function revertToDefaultIfNotPopulated(): bool
```

Tells if the field should be reverted to its default value if it is not populated during validation

Since `1.0`

#### Returns

`boolean` 

---

### setEnabled

```php
public final function setEnabled(bool $enabled)
```

Enables or disables this field

Since `1.0`

#### Parameters

| Name       | Type   | Description |
| ---------- | ------ | ----------- |
| `$enabled` | `bool` |             |

---

### setGenerationWithValue

```php
public final function setGenerationWithValue(bool $enabled)
```

Enables of disables value population during field generation

Since `1.0`

#### Parameters

| Name       | Type      | Description |
| ---------- | --------- | ----------- |
| `$enabled` | `boolean` |             |

---

### setReadOnly

```php
public final function setReadOnly(bool $readOnly)
```

Sets or unsets the field as read only

Since `1.0`

#### Parameters

| Name        | Type   | Description |
| ----------- | ------ | ----------- |
| `$readOnly` | `bool` |             |

---

### setRepeatable

```php
public final function setRepeatable(bool $isRepeatable, int $upTo = -1)
```

Sets or unsets the field as repeatable

Since `1.0`

#### Parameters

| Name            | Type   | Description                                                                          |
| --------------- | ------ | ------------------------------------------------------------------------------------ |
| `$isRepeatable` | `bool` | If set, the field becomes repeatable                                                 |
| `$upTo`         | `int`  | Maximum number of iteration. If 0 or negative, no limit is applied. (Defaults to -1) |

---

### setValue

```php
public function setValue(mixed $value)
```

Sets this field's value

Since `1.0`

#### Parameters

| Name     | Type    | Description |
| -------- | ------- | ----------- |
| `$value` | `mixed` |             |

---

### shouldGenerateWithValue

```php
public final function shouldGenerateWithValue(): bool
```

Tells if the field should be populated with its value when generated

Since `1.0`

#### Returns

`boolean` 

---

### validate

```php
public function validate(bool $silent = false): bool
```

Validates the field's value based on the required flag and the provided filters

Since `1.0`

#### Parameters

| Name      | Type      | Description                                       |
| --------- | --------- | ------------------------------------------------- |
| `$silent` | `boolean` | If set, no error is triggered (defaults to false) |

#### Returns

`boolean` 

---

