# IScriptService Interface

[`chsxf\MFX\Services`](API-Namespace-Services)

```php
interface IScriptService
```

## Summary

Script service interface

Since `2.0`

## Methods

### add

```php
public abstract function add(string $url, bool $inline = false, bool $prepend = false, string $type = 'text/javascript'): void
```

Adds a script to the document

Since `2.0`

#### Parameters

| Name       | Type     | Description                                                                |
| ---------- | -------- | -------------------------------------------------------------------------- |
| `$url`     | `string` | Script URL or path for inline scripts                                      |
| `$inline`  | `string` | If set, the script is included inline in the response (Defaults to false). |
| `$prepend` | `string` | If set, the script is added before any other (Defaults to false).          |
| `$type`    | `string` | Script type (Defaults to text/javascript).                                 |

---

