# IRequestService Interface

[`chsxf\MFX\Services`](API-Namespace-Services)

```php
interface IRequestService
```

## Summary

Request service interface

Since `2.0`

## Methods

### getRequestMethod

```php
public abstract function getRequestMethod(): RequestMethod
```

Get the method used by the request
(ex: GET, POST...)

Since `2.0`

#### Returns

`RequestMethod` 

---

### getRootURL

```php
public abstract function getRootURL(): string
```

Get the root URL for the request

Since `2.0`

#### Returns

`string` 

---

### setAttachmentHeaders

```php
public abstract function setAttachmentHeaders(string $filename, string $mimeType, string $charset = 'UTF-8', bool $addContentType = true): void
```

Sets the attachment headers to use in response to the request

Since `2.0`

#### Parameters

| Name              | Type     | Description                                          |
| ----------------- | -------- | ---------------------------------------------------- |
| `$filename`       | `string` | Filename                                             |
| `$mimeType`       | `string` | MIME type to assign to the response                  |
| `$charset`        | `string` | Charset to use (defaults to UTF-8)                   |
| `$addContentType` | `bool`   | Adds the Content-Type header if set (set by default) |

---

