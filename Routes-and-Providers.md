Routing in MFX is based upon two types of components: **route providers** and **routes**. This section will discuss in detail how to use them to create the various routes your project needs.

## Route Providers

A route provider is a class implementing the `IRouteProvider` interface. You can basically see a route provider as a group of one or more routes.

```php
use chsxf\MFX\Routers\IRouteProvider;

class TestRouteProvider implements IRouteProvider
{
    // ...
}
```

## Routes

Inside a provider, a route is a public static method that is annotated with a `Route` attribute and returns a `RequestResult` object. A route is designed as an endpoint for a request.

```php
use chsxf\MFX\Routers\IRouteProvider;

class TestRouteProvider implements IRouteProvider
{
    #[Route]
    public static function testRoute(): RequestResult
    {
        // ...
    }
}
```

### Route Parameters

A route can receive additional parameters if the method signature includes an array argument.

```php
use chsxf\MFX\Routers\IRouteProvider;

class TestRouteProvider implements IRouteProvider
{
    #[Route]
    public static function testRoute(array $_routeParameters): RequestResult
    {
        // ...
    }
}
```

These parameters are extracted from the route path info, are optional, and different from what you may receive in global arrays like `$_GET` or `$_POST`.

## Matching Routes With Requests

The [next section](Lifecycle-of-a-Request) will explain how requests are handled and matched with the routes that will respond to them.
