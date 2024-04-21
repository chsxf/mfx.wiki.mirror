# StyleSheets Class

[`chsxf\MFX`](API-Namespace-chsxf_MFX)

```php
class StyleSheets
```

## Summary

Helper class for managing style sheets

Since `1.0`

## Methods

### add

```php
public static function add(string $url, string $media = 'screen', bool $inline = false, bool $prepend = false, string $type = 'text/css')
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

#### Throws

| Exception             | Reason                                                                                    |
| --------------------- | ----------------------------------------------------------------------------------------- |
| `StyleSheetException` | If the URL is empty, or if the file does not exists or is not readable for inline sheets. |

---

### export

```php
public static function export(Twig\Environment $twig): string
```

Exports the HTML output for inclusion in the response `<head>` tag

Since `1.0`

#### Parameters

| Name    | Type                | Description                                |
| ------- | ------------------- | ------------------------------------------ |
| `$twig` | `\Twig_Environment` | Twig environnement used for rendering HTML |

#### Returns

`string` 

---

