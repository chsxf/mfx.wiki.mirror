# DateTime Class

[`chsxf\MFX\DataValidator\Fields`](API-Namespace-DataValidator_Fields)

```php
class DateTime extends chsxf\MFX\DataValidator\Field
```

## Summary

Since `1.0`

## Methods

### dateFunctionPattern

```php
public static function dateFunctionPattern(DataValidator\FieldType $type): string
```

Gets the pattern to use with the date() function

Since `1.0`

#### Parameters

| Name    | Type        | Description       |
| ------- | ----------- | ----------------- |
| `$type` | `FieldType` | Type of the field |

#### Returns

`string` 

---

### humanlyReadablePattern

```php
public static function humanlyReadablePattern(DataValidator\FieldType $type): string
```

Gets the pattern as humanly readable

Since `1.0`

#### Parameters

| Name    | Type        | Description       |
| ------- | ----------- | ----------------- |
| `$type` | `FieldType` | Type of the field |

#### Returns

`string` 

---

### regexPattern

```php
public static function regexPattern(DataValidator\FieldType $type, bool $withBackReferences = false): string
```

Gets the pattern as a regular expression

Since `1.0`

#### Parameters

| Name                  | Type        | Description                                                                                     |
| --------------------- | ----------- | ----------------------------------------------------------------------------------------------- |
| `$type`               | `FieldType` | Type of the field                                                                               |
| `$withBackReferences` | `boolean`   | If set, the function should return a regular expression pattern containing name back references |

#### Returns

`string` 

---

