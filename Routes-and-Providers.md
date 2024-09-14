Routing in MFX is based upon two types of components: **route providers** and **routes**. This section will discuss in detail how to use them to create the various routes your project needs.

## Route Providers

A route provider is a class implementing at least the `IRouteProvider` interface. You can basically see a route provider as a group of one or more routes.

```php
use chsxf\MFX\Routers\IRouteProvider;

class TestRouteProvider implements IRouteProvider
{
    // ...
}
```

Alternatively, a route provider can extend the `BaseRouteProvider` class (which itself implements `IRouteProvider`) to gain access to MFX services.

```php
use chsxf\MFX\Routers\BaseRouteProvider;

class TestRouteProvider extends BaseRouteProvider
{
    // ...
}
```

## Routes

A route is designed as an endpoint for a request.

Inside a provider, you define a routes as public methods annotated with a `Route` attribute and that return a `RequestResult` object.

Routes can be either static or instance methods. However, to be able to access MFX services, routes must be instance methods of a class deriving from `BaseRouteProvider`.

```php
use chsxf\MFX\Attributes\Route;
use chsxf\MFX\RequestResult;
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

### Anonymous Routes

By default, an authenticated user is required for every route on your website and access will be denied if none is found. However, you can use the `#[AnonymousRoute]` attribute to allow unauthenticated access on specific routes. You can specify the attribute at the route or the provider level.

```php
#[Route, AnonymousRoute]
public static function testRoute(): RequestResult
{
    // ...
}
```

### Route Parameters

A route can receive additional parameters if the method signature includes an array argument.

```php
use chsxf\MFX\Attributes\Route;
use chsxf\MFX\RequestResult;
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

## Naming

The names of your provider and your route are important in regards of your codebase obviously, but also of the router you will use. Depending of the router you are using, the names may need to match what will exist in the various URLs used in your application.

For example, with the [`PathRouter`](API-Routers-PathRouter), a valid route path is simply the concatenation of both names of the provider and the route, with a forward slash in the middle. In our case here, that would end up being `TestRouteProvider/testRoute`. However, other routers may provide other strategies with different naming schemes.

## Matching Routes With Requests

The [next section](Lifecycle-of-a-Request) will explain how requests are handled and matched with the routes that will respond to them.
