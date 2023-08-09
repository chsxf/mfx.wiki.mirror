# Summary

Class containing utility functions for encoding data in XML

# Namespace

`chsxf\MFX`

# Methods

## build

`public static function build(mixed $var, string $encoding = UTF-8): string`

Build XML tree from a variable

### Parameters

| Name        | Type     | Description                               |
| ----------- | -------- | ----------------------------------------- |
| `$var`      | `mixed`  | Variable from which building the XML tree |
| `$encoding` | `string` | Encoding charset (Defaults to UTF-8).     |

### Returns

`string` the XML tree string
