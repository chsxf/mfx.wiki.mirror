# CoreManager Class

[`chsxf\MFX`](API-Namespace-chsxf_MFX)

```php
final class CoreManager implements Services\IRequestService, Services\ITemplateService
```

## Summary

Core manager class

Handles requests and responses.

Since `1.0`

## Constants

```php
public const HTML_CONTENT_TYPE = 'text/html';
```

Since `1.0`

## Methods

### __construct

```php
public function __construct(ErrorManager $errorManager, Services\IConfigService $configService, Services\ILocalizationService $localizationService, Services\IProfilingService $profilingService, Services\IAuthenticationService $authenticationService, Services\IDatabaseService $databaseService, Services\ISessionService $sessionService)
```

Constructor

Since `2.0`

#### Parameters

| Name                     | Type                     | Description                     |
| ------------------------ | ------------------------ | ------------------------------- |
| `$errorManager`          | `ErrorManager`           | Error manager instance          |
| `$configService`         | `IConfigService`         | Config service instance         |
| `$localizationService`   | `ILocalizationService`   | Localization service instance   |
| `$profilingService`      | `IProfilingService`      | Profiling service instance      |
| `$authenticationService` | `IAuthenticationService` | Authentication service instance |
| `$databaseService`       | `IDatabaseService`       | Database service instance       |
| `$sessionService`        | `ISessionService`        | Session service instance        |

---

### convertFakeProtocols

```php
public function convertFakeProtocols(string $str): string
```

Converts the fake protocols in the input strings

Since `2.0`

#### Parameters

| Name   | Type     | Description  |
| ------ | -------- | ------------ |
| `$str` | `string` | Input string |

#### Returns

`string` 

---

### getRequestContentType

```php
public function getRequestContentType(): ?string
```

Get the content-type used by the request
(ex: application/json)

Since `2.0.1`

#### Returns

`null|string` 

---

### getRequestMethod

```php
public function getRequestMethod(): RequestMethod
```

Get the method used by the request
(ex: GET, POST...)

Since `2.0`

#### Returns

`RequestMethod` 

---

### getRootURL

```php
public function getRootURL(): string
```

Builds the root URL from server information (protocol, host and PHP_SELF)

Since `2.0`

#### Returns

`string` 

---

### getTwig

```php
public function getTwig(): ?Twig\Environment
```

Gets the Twig environment for the current request

Since `2.0`

#### Returns

`\Twig\Environment` 

---

### setAttachmentHeaders

```php
public function setAttachmentHeaders(string $filename, string $mimeType, string $charset = 'UTF-8', bool $addContentType = true): void
```

Sets attachment headers for file downloads

Since `2.0`

#### Parameters

| Name              | Type     | Description                                                                                                                       |
| ----------------- | -------- | --------------------------------------------------------------------------------------------------------------------------------- |
| `$filename`       | `string` | Downlaoded file name                                                                                                              |
| `$mimeType`       | `string` | Attachment MIME type. This parameter is ignored if $addContentType is not set.                                                    |
| `$charset`        | `string` | Attachment charset. If NULL, no charset is provided. This parameter is ignored if $addContentType is not set. (Defaults to UTF-8) |
| `$addContentType` | `bool`   | If set, the function will add the Content-Type header. (Defaults to true)                                                         |

---

