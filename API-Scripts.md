# Scripts Class

[`chsxf\MFX`](API-Namespace-chsxf_MFX)

```php
final class Scripts implements Services\IScriptService
```

## Summary

Helper class for managing scripts

Since `1.0`

## Constants

```php
public const DEFAULT_TYPE = 'text/javascript';
```

Since `2.0`

## Methods

### __construct

```php
public function __construct(Services\ITemplateService $templateService)
```

Since `1.0`

---

### add

```php
public function add(string $url, bool $inline = false, bool $prepend = false, string $type = 'self::DEFAULT_TYPE', array $extras = array()): void
```

Adds a script to the document

Since `1.0`

#### Parameters

| Name       | Type     | Description                                                                |
| ---------- | -------- | -------------------------------------------------------------------------- |
| `$url`     | `string` | Script URL or path for inline scripts                                      |
| `$inline`  | `string` | If set, the script is included inline in the response (Defaults to false). |
| `$prepend` | `string` | If set, the script is added before any other (Defaults to false).          |
| `$type`    | `string` | Script type (Defaults to text/javascript).                                 |
| `$extras`  | `array`  | Extra arguments to add to the script tag                                   |

#### Throws

| Exception         | Reason                                                                                     |
| ----------------- | ------------------------------------------------------------------------------------------ |
| `ScriptException` | If the URL is empty, or if the file does not exists or is not readable for inline scripts. |

---

### export

```php
public function export(): string
```

Exports the HTML output for inclusion in the response `<head>` tag

Since `1.0`

#### Returns

`string` 

---

