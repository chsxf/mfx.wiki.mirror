The Request Service provides information about the root URL of the server and allows you to control attachment headers.

It implements the `IRequestService` interface.

## Access Root URL

```php
function getRootURL(): string;
```

## Controlling Attachment Headers

```php
function setAttachmentHeaders(string $filename, string $mimeType, string $charset = 'UTF-8', bool $addContentType = true): void;
```
