# StyleSheets Class

[`chsxf\MFX`](API-Namespace-chsxf_MFX)

```php
final class StyleSheets implements Services\IStyleSheetService
```

## Summary

Helper class for managing style sheets

Since `1.0`

## Constants

```php
public const DEFAULT_MEDIA = 'screen';
```

Since `2.0`

```php
public const DEFAULT_TYPE = 'text/css';
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
public function add(string $url, string $media = 'self::DEFAULT_MEDIA', bool $inline = false, bool $prepend = false, string $type = 'self::DEFAULT_TYPE', array $extras = array()): void
```

Adds a style sheets to the document

Since `1.0`

#### Parameters

| Name       | Type     | Description                                                                     |
| ---------- | -------- | ------------------------------------------------------------------------------- |
| `$url`     | `string` | Style sheet URL or path for inline sheets                                       |
| `$media`   | `string` | Media type (Defaults to screen)                                                 |
| `$inline`  | `bool`   | If set, the style sheet is included inline in the response (Defaults to false). |
| `$prepend` | `bool`   | If set, the style sheet is added before any other (Defaults to false).          |
| `$type`    | `string` | Style sheet type (Defaults to text/css).                                        |
| `$extras`  | `array`  | Extra arguments                                                                 |

#### Throws

| Exception             | Reason                                                                                    |
| --------------------- | ----------------------------------------------------------------------------------------- |
| `StyleSheetException` | If the URL is empty, or if the file does not exists or is not readable for inline sheets. |

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

