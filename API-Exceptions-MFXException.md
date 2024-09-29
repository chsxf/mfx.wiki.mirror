# MFXException Class

[`chsxf\MFX\Exceptions`](API-Namespace-Exceptions)

```php
class MFXException extends Exception
```

## Summary

Base exception class for all MFX code

Since `2.0`

## Methods

### __construct

```php
public function __construct(HttpStatusCodes $code = 'chsxf\MFX\HttpStatusCodes::badRequest', string $message = '', ?Throwable $previous = null)
```

Constructor

Since `2.0`

#### Parameters

| Name        | Type              | Description                                                                |
| ----------- | ----------------- | -------------------------------------------------------------------------- |
| `$code`     | `HttpStatusCodes` | HTTP status code associated to the Exception (defaults to 400 Bad Request) |
| `$message`  | `string`          | The exception message                                                      |
| `$previous` | `null|Throwable`  | The previously thrown exception                                            |

---

### getHttpCode

```php
public function getHttpCode(): HttpStatusCodes
```

Returns the HTTP status code associated with the exception

Since `2.0`

#### Returns

`HttpStatusCodes` 

---

