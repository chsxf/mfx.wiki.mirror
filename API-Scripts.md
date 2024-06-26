# Scripts Class

[`chsxf\MFX`](API-Namespace-chsxf_MFX)

```php
class Scripts
```

## Summary

Helper class for managing scripts

Since `1.0`

## Methods

### add

```php
public static function add(string $url, bool $inline = false, bool $prepend = false, string $type = 'text/javascript')
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

#### Throws

| Exception         | Reason                                                                                     |
| ----------------- | ------------------------------------------------------------------------------------------ |
| `ScriptException` | If the URL is empty, or if the file does not exists or is not readable for inline scripts. |

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

