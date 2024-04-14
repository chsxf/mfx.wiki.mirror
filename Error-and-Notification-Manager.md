As for many other things, error management in MFX is mostly automated.

## Errors

Errors triggered during the execution of your scripts will be catched by MFX's Error Manager and included in a specific part of the page template.

You can also call PHP's native [`trigger_error`](https://www.php.net/manual/en/function.trigger-error.php) function to raise a custom error on your side.

The Error Manager will comply with the current error reporting level, as any error handler would do.

## Notifications

In complement of errors, MFX also handles notifications. Different to errors, notifications are only string messages and do not carry any other context information. But they are obviously useful to provide information to the user when some operations are carried.

Just like errors, notifications are handled automatically by the Error Manager and output in a specific part of the page template.

You can trigger a notification using the following method:

```php
trigger_notif(string $message)
```

## Error Management and Sessions

It is common for errors and notifications to be raised during a request, with the web server redirecting to a new page to display relevant information.

In order to avoid losing track of any error or notification, the status of the Error Manager is "freezed" (or serialized) into the current session before the redirection and "unfreezed" (or deserialized) on the next request.

Errors and notifications are cleared out as soon as the content of the Error Manager is flushed out to the web page.

## Flushing Out

In a normal workflow, MFX takes care of flushing out errors and notifications for all `VIEW`, `JSON` and `XML` requests (see [[Request Results]]). This is also true for `STATUS` requests that output JSON or XML content.

However, for other content types, you would need to flush out errors and notifications yourself.

You may want to either flush out to an array or object, to a Twig environment, or to nothing (effectively discarding raised errors and notifications). Use either of these functions:

```php
/**
 * Flushes error and notification messages to an array or an object
 * @param array|object $arrOrObject Array or object to modify
 */
ErrorManager::flushToArrayOrObject(array|object &$arrOrObject)

/**
 * Flushes error and notification messages for template display
 * @param \Twig_Environment $twig Twig environment. If NULL, the function flushes containers only and returns an empty string
 * @return string
 */
ErrorManager::flush(?Environment $twig = NULL): string
```
