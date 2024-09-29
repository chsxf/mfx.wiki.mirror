MFX provides with the Script Service a convenient way to include scripts in your web pages. They can be registered for global use or selectively with each route.

The Script Service implements the `IScriptService` interface.

## Using Scripts Globally

You can register scripts globally using the `scripts` [configuration directive](Configuration-Directives#assets-management).

Scripts appearing in the configuration directive will be present on every page your app will produce.

However, they will all appear as external resources. If for some reason, you need one of your script to be inlined in all web pages, you need to use a [pre-route callback](Lifecycle-of-a-Request#3-calling-pre-processing-callbacks) applied to every route and register it manually as described below.

## Using Scripts Selectively

Routes can register scripts manually thanks to the following function:

```php
function add(string $url,
             bool $inline = false,
             bool $prepend = false,
             string $type = 'text/javascript')
```

|  Parameter | Description                                                                                 |
| ---------- | ------------------------------------------------------------------------------------------- |
| `$url`     | URL of the script you want to register. You can use [[Fake Protocols]].                     |
| `$inline`  | If true, the script will be inlined in the web page instead of being referenced by its URL. |
| `$prepend` | If true, the script will be registered before any other script already registered.          |
| `$type`    | In case your script is not JavaScript, you can override the type with this parameter.       |
