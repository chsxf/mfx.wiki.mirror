As explained in the [[Building Your First Route]] tutorial, declaring a basic route in MFX is possible thanks to the `IRouteProvider` interface and the `#[Route]` attribute.

However, in many occasions, you want to customize the behavior of a route, either by limiting the kind of request it can handle, or how the response will be produced.

This page will introduce you to the all the built-in attributes and [[configuration directives]] designed for that purpose.

## Global Configuration Directives

The configuration directives [related to the Core Manager](Configuration-Directives#core-manager) can determine the way routes behave. However, these directives are applied globally to all routes, defining in essence the default behavior.

## Route-Level Configuration

In complement of the global configuration directives, you can fine tune every route behavior thanks to [attributes](https://www.php.net/manual/en/language.attributes.php).

Some attributes can be applied only to a route, but others can also be applied to the route provider itself.

Attributes are divided into three categories: those validating the request, others handling the response, and finally callbacks.

### Usage Example

```php
<?php
use chsxf\MFX\Attributes\AnonymousRoute;
use chsxf\MFX\Attributes\ContentType;
use chsxf\MFX\Attributes\RequireRequestMethod;
use chsxf\MFX\Attributes\Route;
use chsxf\MFX\Routers\IRouteProvider;
use chsxf\MFX\RequestMethod;
use chsxf\MFX\RequestResult;

#[AnonymousRoute]
class TestRoute implements IRouteProvider
{
    #[Route, ContentType('text/plain'), RequireRequestMethod(RequestMethod::GET)]
    public static function hello(): RequestResult {
        echo 'Hello, world!';
        exit();
    }
}
```

### Request Attributes

| Attribute                  | Description                                                                                                                        | Targets                 | Parameters                                           |
| -------------------------- | ---------------------------------------------------------------------------------------------------------------------------------- | ----------------------- | ---------------------------------------------------- |
| `#[AnonymousRoute]`        | If this attribute is present, the route can be reached even if no user is signed in. See [[User Management]] for more information. | Routes, Route providers |                                                      |
| `#[RequireContentType]`    | If this attribute is present, the request content type must match the specified one.                                               | Routes                  | `string $value`: the required content type           |
| `#[RequiredRequestMethod]` | If this attribute is present, the request method must match the specified one.                                                     | Routes                  | `RequestMethod $_requestMethod`: the required method |

### Response Attributes

| Attribute        | Description                                                                                                                                                                                          | Targets                 | Parameters                                   |
| ---------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------- | -------------------------------------------- |
| `#[ContentType]` | If this attribute is present, the response will use the specific content type.                                                                                                                       | Routes, Route providers | `string $value`: the response's content type |
| `#[RedirectURL]` | If this attribute is present, every `REDIRECT` [request result](Request-Results) from the corresponding routes that do not provide a redirection URL will use the one specified with this attribute. | Routes, Route providers | `string $value`: the redirection URL         |
| `#[Template]`    | If this attribute is present, the response will use the specified Twig template by default.                                                                                                          | Routes                  | `string $value`: the Twig template path      |

### Callback Attributes

Callback attributes can be used to call functions before and after the execution of a route. As with the configuration directives, there are pre- and post-route callbacks.

Pass a static [callable](https://www.php.net/manual/en/language.types.callable.php) to either of the `#[PreRouteCallback]` or the `#[PostRouteCallback]` attributes to respectively execute the corresponding function before or after the route.

Both attributes can be specified at the route or the route provider level, and they are cumulative. Therefore, you can execute up to three pre- or post-route callbacks for some routes, in the following order:

- Global pre-route callback
- Route provider level pre-route callback
- Route level pre-route callback
  - _(Execution of the route code)_
- Route level post-route callback
- Route provider level post-route callback
- Global post-route callback
