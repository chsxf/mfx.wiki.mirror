# ArrayTools Class

[`chsxf\MFX`](API-Namespace-chsxf_MFX)

```php
final class ArrayTools
```

## Summary

Array helpers

Since `1.0`

## Methods

### concatArrays

```php
public static function concatArrays(mixed ...$arguments): array
```

Concatenate values together into a new array without considering keys or types.

The function accepts unlimited arguments.
However, if a single array argument is passed, it is used as an array of arguments, thus its content will be concatenated and the array itself.

Since `1.0`

#### Returns

`array` 

---

### isParameterArray

```php
public static function isParameterArray(ReflectionParameter $parameter): bool
```

Checks if the parameter is an array or a union type accepting an array

Since `1.0`

#### Parameters

| Name         | Type                   | Description                  |
| ------------ | ---------------------- | ---------------------------- |
| `$parameter` | `\ReflectionParameter` | The parameter to investigate |

#### Returns

`bool` 

---

### reverseArrays

```php
public static function reverseArrays(array $store): array
```

Reverses dimensions of the source array.

The result array is built using the keys of the contained arrays, each referencing a new array.
Each related row value is then added in the corresponding array.

This function is useful to convert database rows to HTML form data.

Note:
It is assumed that all contained arrays use the same keys.

Since `1.0`

#### Parameters

| Name     | Type    | Description  |
| -------- | ------- | ------------ |
| `$store` | `array` | Source array |

#### Returns

`array` 

---

### shuffle

```php
public static function shuffle(array &$arr)
```

Shuffles the content of an array

Since `1.0`

#### Parameters

| Name   | Type    | Description |
| ------ | ------- | ----------- |
| `$arr` | `array` |             |

---

