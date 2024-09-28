MFX provides with the Stylesheet Service a convenient way to include stylesheets in your web pages. They can be registered for global use or selectively with each route.

The Stylesheet Service implements the `IStyleSheetService` interface.

## Using Stylesheets Globally

You can register stylesheets globally using the `stylesheets` [configuration directive](Configuration-Directives#assets-management).

Stylesheets appearing in the configuration directive will be present on every page your app will produce.

However, they will all appear as external resources. If for some reason, you need one of your stylesheet to be inlined in all web pages, you need to use a [pre-route callback](Lifecycle-of-a-Request#3-calling-pre-processing-callbacks) applied to every route and register it manually as described below.

## Using Stylesheets Selectively

Routes can register stylesheets manually thanks to the following function:

```php
function add(string $url,
                 string $media = 'screen',
                 bool $inline = false,
                 bool $prepend = false,
                 string $type = 'text/css')
```

|  Parameter | Description                                                                                     |
| ---------- | ----------------------------------------------------------------------------------------------- |
| `$url`     | URL of the stylesheet you want to register. You can use [[Fake Protocols]].                     |
| `$media`   | Type of media your stylesheet is dedicated to. Defaults to `screen`.                            |
| `$inline`  | If true, the stylesheet will be inlined in the web page instead of being referenced by its URL. |
| `$prepend` | If true, the stylesheet will be registered before any other stylesheet already registered.      |
| `$type`    | In case your stylesheet is not CSS, you can override the type with this parameter.              |
