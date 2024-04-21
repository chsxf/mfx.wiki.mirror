# CoreManager Class

[`chsxf\MFX`](API-Namespace-chsxf_MFX)

```php
final class CoreManager
```

## Summary

Core manager singleton class

Handles all requests and responses.

Since `1.0`

## Methods

### convertFakeProtocols

```php
public static function convertFakeProtocols(string $str): string
```

Converts the fake protocols in the input strings

Since `1.0`

#### Parameters

| Name   | Type     | Description  |
| ------ | -------- | ------------ |
| `$str` | `string` | Input string |

#### Returns

`string` 

---

### dieWithStatusCode

```php
public static function dieWithStatusCode(int $code = 400, ?string $message = null)
```

Terminates the script and emits a HTTP status code

Since `1.0`

#### Parameters

| Name       | Type      | Description                                            |
| ---------- | --------- | ------------------------------------------------------ |
| `$code`    | `int`     | HTTP status code to emit (Defaults to 400 Bad Request) |
| `$message` | `?string` | Custom message to output with status code              |

---

### flushAllOutputBuffers

```php
public static function flushAllOutputBuffers()
```

Flushes all output buffers

Since `1.0`

---

### getRootURL

```php
public static function getRootURL(): string
```

Builds the root URL from server information (protocol, host and PHP_SELF)

Since `1.0`

#### Returns

`string` 

---

### getTwig

```php
public static function getTwig(): ?Twig\Environment
```

Gets the Twig environment for the current request

Since `1.0`

#### Returns

`\Twig\Environment` 

---

### redirect

```php
public static function redirect(?string $redirectURL = null)
```

Redirects the user the specified URL, the HTTP referer if defined and same host or the website root

Since `1.0`

#### Parameters

| Name           | Type     | Description                               |
| -------------- | -------- | ----------------------------------------- |
| `$redirectURL` | `string` | Target redirection URL (Defaults to NULL) |

---

### setAttachmentHeaders

```php
public static function setAttachmentHeaders(string $filename, string $mimeType, string $charset = 'UTF-8', bool $addContentType = true)
```

Sets attachment headers for file downloads

Since `1.0`

#### Parameters

| Name              | Type     | Description                                                                                                                       |
| ----------------- | -------- | --------------------------------------------------------------------------------------------------------------------------------- |
| `$filename`       | `string` | Downlaoded file name                                                                                                              |
| `$mimeType`       | `string` | Attachment MIME type. This parameter is ignored if $addContentType is not set.                                                    |
| `$charset`        | `string` | Attachment charset. If NULL, no charset is provided. This parameter is ignored if $addContentType is not set. (Defaults to UTF-8) |
| `$addContentType` | `bool`   | If set, the function will add the Content-Type header. (Defaults to true)                                                         |

---

