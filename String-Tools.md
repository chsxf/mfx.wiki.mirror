# Summary

String management helper class

# Namespace

`chsxf\MFX`

# Methods

## generateRandomString

`public static function generateRandomString(int $length, string $charset = self::CHARSET_ALPHANUMERIC_LC): string|false`

Generates a random string based on the specified character set

### Parameters

| Name       | Type     | Description                                                    |
| ---------- | -------- | -------------------------------------------------------------- |
| `$length`  | `int`    | Length of the resulting string                                 |
| `$charset` | `string` | Character set (Defaults to alphanumeric lower case characters) |

### Returns

`boolean|string` Returns false if length is zero or negative or charset is not a non-empty string. Returns the generated string either.

## implode

`public static function implode(string $separator, array $elements, ?string $lastSeparator = null, ?string $firstSeparator = null): string`

Joins array elements with a separator string, eventually replacing the first and last separators with specific ones.

### Parameters

| Name              | Type     | Description                                                                                                                                           |
| ----------------- | -------- | ----------------------------------------------------------------------------------------------------------------------------------------------------- |
| `$separator`      | `string` | Separator string                                                                                                                                      |
| `$elements`       | `array`  | Elements to join. If $elements is empty, the function returns an empty string. If $elements contains only one element, function returns this element. |
| `$lastSeparator`  | `string` | Separator to use between the two last elements. If NULL, the general separator is used. (Defaults to NULL)                                            |
| `$firstSeparator` | `string` | Separator to use between the two first elements. If NULL, the general separator is used. (Defaults to NULL)                                           |

### Returns

`string` Note :

## isInteger

`public static function isInteger(string $str): bool`

Checks if the specified string contains an integer

### Parameters

| Name   | Type     | Description        |
| ------ | -------- | ------------------ |
| `$str` | `string` | String to evaluate |

### Returns

`boolean` 

## isNegativeInteger

`public static function isNegativeInteger(string $str, bool $canBeZero = ): bool`

Checks if the specified string contains a negative integer, optionnaly equals to zero

### Parameters

| Name         | Type      | Description                                                                                            |
| ------------ | --------- | ------------------------------------------------------------------------------------------------------ |
| `$str`       | `string`  | String to evaluate                                                                                     |
| `$canBeZero` | `boolean` | If set, the string can be evaluated to zero. If not, the integer must be negative. (Defaults to false) |

### Returns

`boolean` 

## isPositiveInteger

`public static function isPositiveInteger(string $str, bool $canBeZero = ): bool`

Checks if the specified string contains a positive integer, optionnaly equals to zero

### Parameters

| Name         | Type      | Description                                                                                            |
| ------------ | --------- | ------------------------------------------------------------------------------------------------------ |
| `$str`       | `string`  | String to evaluate                                                                                     |
| `$canBeZero` | `boolean` | If set, the string can be evaluated to zero. If not, the integer must be positive. (Defaults to false) |

### Returns

`boolean` 

## isValidEmailAddress

`public static function isValidEmailAddress(string $address): bool`

Checks if the specified address is a valid email address

### Parameters

| Name       | Type     | Description                       |
| ---------- | -------- | --------------------------------- |
| `$address` | `string` | The email address string to check |

### Returns

`boolean` true if the address is valid, false either

## removeAccents

`public static function removeAccents(string $string): string`

Removes accents from accented characters

### Parameters

| Name      | Type     | Description   |
| --------- | -------- | ------------- |
| `$string` | `string` | Source string |

### Returns

`string` 

## sanitize

`public static function sanitize(string $string, string $placeholder = -): string`

Sanitizes a string by removing accents, then transforming to lower case,
then replacing non-alphabetic and non-numeric characters by a place holder,
then removing consecutive multiple place holders.
Note:
Result string may start or end with the place holder.

### Parameters

| Name           | Type     | Description                        |
| -------------- | -------- | ---------------------------------- |
| `$string`      | `string` | Source string                      |
| `$placeholder` | `string` | Placeholder text (Defaults to '-') |

### Returns

`string` 

## snakeToCamelCase

`public static function snakeToCamelCase(string $_str): string`

Converts a string in snake case to the same string in camel case

### Parameters

| Name    | Type     | Description  |
| ------- | -------- | ------------ |
| `$_str` | `string` | Input string |

### Returns

`string` Resulting string in camel case

## snakeToPascalCase

`public static function snakeToPascalCase(string $_str): string`

Converts a string in snake case to the same string in Pascal case

### Parameters

| Name    | Type     | Description  |
| ------- | -------- | ------------ |
| `$_str` | `string` | Input string |

### Returns

`string` Resulting string in Pascal case

## toSnakeCase

`public static function toSnakeCase(string $_str, bool $_upperCase = ): string`

Converts a string in snake case

### Parameters

| Name          | Type     | Description                                     |
| ------------- | -------- | ----------------------------------------------- |
| `$_str`       | `string` | Input string                                    |
| `$_upperCase` | `bool`   | If set, returns the string in upper snake case. |

### Returns

`string` Resulting string in snake case

