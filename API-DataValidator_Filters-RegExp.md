# RegExp Class

[`chsxf\MFX\DataValidator\Filters`](API-Namespace-DataValidator_Filters)

```php
class RegExp extends chsxf\MFX\DataValidator\AbstractFilter
```

## Summary

Descriptor of a filter field based on regular expressions

Since `1.0`

## Constants

```php
public const REGEX_WORD = '/^[a-z0-9_]+$/i';
```

```php
public const REGEX_LCWORD = '/^[a-z0-9_]+$/';
```

```php
public const REGEX_UCWORD = '/^[A-Z0-9_]+$/';
```

```php
public const REGEX_LCALPHANUMERIC = '/^[a-z0-9]+$/';
```

```php
public const REGEX_UCALPHANUMERIC = '/^[A-Z0-9]+$/';
```

```php
public const REGEX_LCHEXADECIMAL = '/^[a-f0-9]+$/';
```

```php
public const REGEX_UCHEXADECIMAL = '/^[A-F0-9]+$/';
```

```php
public const REGEX_ICHEXADECIMAL = '/^[a-f0-9]+$/i';
```

```php
public const REGEX_SQL_DATETIME = '/^\d{4}-\d{2}-\d{2} \d{2}:\d{2}:\d{2}$/';
```

## Methods

### __construct

```php
public function __construct(string $regexp, ?string $message = null)
```

Constructor

See `preg_match()`

Since `1.0`

#### Parameters

| Name       | Type     | Description                               |
| ---------- | -------- | ----------------------------------------- |
| `$regexp`  | `string` | Perl-Compatible regular expression (PCRE) |
| `$message` | `string` | Error message                             |

---

### equals

```php
public static function equals(string $value, bool $caseInsensitive = false): RegExp
```

Helper function to build a equality validation filter

Since `1.0`

#### Parameters

| Name     | Type     | Description          |
| -------- | -------- | -------------------- |
| `$value` | `string` | Exact value to match |

#### Returns

`RegExp` 

---

### hexKey

```php
public static function hexKey(int $_bitLength, bool $_ignoreCase = false, bool $_lowerCase = true): RegExp
```

Helper function to build variable bit-length hexadecimal key validation filter

Since `1.0`

#### Parameters

| Name           | Type   | Description                                                                                                                                                                 |
| -------------- | ------ | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `$_bitLength`  | `int`  | Bit-length of the key (must be a multiple of 8)                                                                                                                             |
| `$_ignoreCase` | `bool` | If set, produces a case-insensitive validation filter                                                                                                                       |
| `$_lowerCase`  | `bool` | If set and case is not ignored, the validation filter will constrain to lower case. If not set and case is not ignored, the validation filter will constrain to upper case. |

#### Returns

`RegExp` 

---

### lowerCaseWord

```php
public static function lowerCaseWord(): RegExp
```

Helper function to build lower case validation filter

Since `1.0`

#### Returns

`RegExp` 

---

### stringLength

```php
public static function stringLength(?int $min = null, ?int $max = null): RegExp
```

Helper function to build string length validation filters

Since `1.0`

#### Parameters

| Name   | Type  | Description                                                                               |
| ------ | ----- | ----------------------------------------------------------------------------------------- |
| `$min` | `int` | Minimum required length. If empty or negative, no minimum is required. (Defaults to NULL) |
| `$max` | `int` | Maximum required length. If empty or negative, no maximum is required. (Defaults to NULL) |

#### Returns

`RegExp` 

---

### upperCaseWord

```php
public static function upperCaseWord(): RegExp
```

Helper function to build upper case validation filter

Since `1.0`

#### Returns

`RegExp` 

---

### word

```php
public static function word(): RegExp
```

Helper function to build case-insensitive word validation filter

Since `1.0`

#### Returns

`RegExp` 

---

