# IStyleSheetService Interface

[`chsxf\MFX\Services`](API-Namespace-Services)

```php
interface IStyleSheetService
```

## Summary

StyleSheet service interface

Since `2.0`

## Methods

### add

```php
public abstract function add(string $url, string $media = 'screen', bool $inline = false, bool $prepend = false, string $type = 'text/css'): void
```

Adds a style sheets to the document

Since `2.0`

#### Parameters

| Name       | Type     | Description                                                                     |
| ---------- | -------- | ------------------------------------------------------------------------------- |
| `$url`     | `string` | Style sheet URL or path for inline sheets                                       |
| `$media`   | `string` | Media type (Defaults to screen)                                                 |
| `$inline`  | `bool`   | If set, the style sheet is included inline in the response (Defaults to false). |
| `$prepend` | `bool`   | If set, the style sheet is added before any other (Defaults to false).          |
| `$type`    | `string` | Style sheet type (Defaults to text/css).                                        |

---

