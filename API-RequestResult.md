# RequestResult Class

[`chsxf\MFX`](API-Namespace-chsxf_MFX)

```php
final class RequestResult
```

## Summary

Class holding data and information about the request response

Since `1.0`

## Methods

### __construct

```php
public function __construct(?RequestResultType $type = null, mixed $data = null, ?string $template = null, ?string $redirectURL = null, HttpStatusCodes $statusCode = 'chsxf\MFX\HttpStatusCodes::ok', bool $preformatted = false)
```

Constructor

Some parameters, such as $template, may be automatically defined in the route function attributes
but can be overridden through this constructor if needed.

See `RequestResultType`

Since `2.0`

#### Parameters

| Name            | Type                | Description                                                                                                               |
| --------------- | ------------------- | ------------------------------------------------------------------------------------------------------------------------- |
| `$type`         | `RequestResultType` | Request result type. If NULL, the type defaults to VIEW. (Defaults to NULL)                                               |
| `$data`         | `mixed`             | Response data. If a view, $data must be an array. (Defaults to NULL)                                                      |
| `$template`     | `string`            | Template to use as the response renderer. Don't add the .twig extension. Should be NULL if not a view. (Defaults to NULL) |
| `$redirectURL`  | `string`            | Target URL to which redirect the user (Defaults to NULL)                                                                  |
| `$statusCode`   | `HttpStatusCodes`   | HTTP status code of the response (Defaults to 200 - OK).                                                                  |
| `$preformatted` | `boolean`           | If set, this flag indicates that $data is preformatted for XML and JSON responses. (Defaults to false)                    |

---

### addViewGlobal

```php
public static function addViewGlobal(string $name, mixed $value)
```

Add a VIEW global value

Since `1.0`

#### Parameters

| Name     | Type     | Description              |
| -------- | -------- | ------------------------ |
| `$name`  | `string` | Name of the global value |
| `$value` | `mixed`  | Value                    |

---

### buildJSONRequestResult

```php
public static function buildJSONRequestResult(mixed $data, bool $preformatted = false, HttpStatusCodes $statusCode = 'chsxf\MFX\HttpStatusCodes::ok'): RequestResult
```

Helper function to build RequestResult instances for JSON responses

Since `2.0`

#### Parameters

| Name            | Type              | Description                                   |
| --------------- | ----------------- | --------------------------------------------- |
| `$data`         | `mixed`           | JSON data                                     |
| `$preformatted` | `bool`            | If set, $data contains preformatted JSON data |
| `$statusCode`   | `HttpStatusCodes` | HTTP status code of the response              |

#### Returns

`RequestResult` 

---

### buildRedirectRequestResult

```php
public static function buildRedirectRequestResult(?string $redirectURL = null): RequestResult
```

Helper function to build RequestResult instances for REDIRECT request results

Since `1.0`

#### Parameters

| Name           | Type     | Description                                              |
| -------------- | -------- | -------------------------------------------------------- |
| `$redirectURL` | `string` | Target URL to which redirect the user (Defaults to NULL) |

#### Returns

`RequestResult` 

---

### buildStatusRequestResult

```php
public static function buildStatusRequestResult(HttpStatusCodes $statusCode = 'chsxf\MFX\HttpStatusCodes::badRequest', ?string $message = null): RequestResult
```

Helper function to build RequestResult instances for erroneous responses, providing the HTTP status code

Since `2.0`

#### Parameters

| Name          | Type              | Description                      |
| ------------- | ----------------- | -------------------------------- |
| `$statusCode` | `HttpStatusCodes` | HTTP status code of the response |
| `$message`    | `?string`         | Message                          |

#### Returns

`RequestResult` 

---

### buildXMLRequestResult

```php
public static function buildXMLRequestResult(mixed $data, bool $preformatted = false, HttpStatusCodes $statusCode = 'chsxf\MFX\HttpStatusCodes::ok'): RequestResult
```

Helper function to build RequestResult instances for XML responses

Since `2.0`

#### Parameters

| Name            | Type              | Description                                  |
| --------------- | ----------------- | -------------------------------------------- |
| `$data`         | `mixed`           | XML data                                     |
| `$preformatted` | `bool`            | If set, $data contains preformatted XML data |
| `$statusCode`   | `HttpStatusCodes` | HTTP status code of the response             |

#### Returns

`RequestResult` 

---

### data

```php
public function data(): mixed
```

Gets the data generated by the response

Since `1.0`

#### Returns

`mixed` 

---

### getViewGlobals

```php
public static function getViewGlobals(): array
```

Gets all VIEW global values

Since `1.0`

#### Returns

`array` 

---

### preformatted

```php
public function preformatted(): bool
```

Tells if the data is preformmated or not for XML and JSON repsonses

Since `1.0`

#### Returns

`boolean` 

---

### redirectURL

```php
public function redirectURL(): ?string
```

Gets the redirection URL if existing

Since `1.0`

#### Returns

`string` 

---

### removeViewGlobal

```php
public static function removeViewGlobal(string $name)
```

Remove a VIEW global value

Since `1.0`

#### Parameters

| Name    | Type     | Description                  |
| ------- | -------- | ---------------------------- |
| `$name` | `string` | Name of the global to remove |

---

### statusCode

```php
public function statusCode(): HttpStatusCodes
```

Gets the HTTP status code of the response

Since `2.0`

#### Returns

`HttpStatusCodes` 

---

### template

```php
public function template(?string $defaultValue = null): string
```

Gets the template to use as the response renderer

Since `1.0`

#### Parameters

| Name            | Type     | Description                                                                               |
| --------------- | -------- | ----------------------------------------------------------------------------------------- |
| `$defaultValue` | `string` | Default template name if none provided. Don't add the .twig extension. (Defaults to NULL) |

#### Returns

`string` 

---

### type

```php
public function type(): RequestResultType
```

Gets the request result type

Since `1.0`

#### Returns

`RequestResultType` 

---

