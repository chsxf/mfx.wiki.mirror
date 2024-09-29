Routing in MFX is handled by router classes, that will identify a route provider and a route from the request URL, as explained in the [[Routes and Providers]] and [[Lifecycle of a Request]] pages.

MFX provides two built-in router classes, the default `PathRouter` and the `MainSubRouter`. Both work similarly and the only difference resides in the syntax of the route. `PathRouter` except the route to be declared as `provider/route` whereas `MainSubRouter` expects it to be `provider.route`.

However, these two routers may not address your specific needs. Then, you will have to create your own router.

## Creating a Custom Router

A router is a class implementing the [`IRouter`](API-Routers-IRouter) interface, which includes only a single function called `parseRoute(...)` and that returns a [`RouterData`](API-Routers-RouterData) object.

> [!TIP]
> Look at [existing routers](https://github.com/chsxf/mfx/tree/main/src/Routers) to learn more about how to handle routing.

A RouterData object contains information that will be used by the Core Manager to process the request:

- The route that is currently called as a string (ie `testroute/hello`)
- The attributes associated with the route provider class
- The attributes associated with the route method (will contain at least the `Route` attribute)
- An array containing the various route parameters for the request (see more below)
- The `ReflectionMethod` instance of the route method
- The default template file to use with the route

Finally you will need to assign your custom router in the configuration file thanks to the [`router.class` configuration directive](Configuration-Directives#routers).

### Route Parameters

Routes can be called with parameters and these parameters will be passed through the RouterData object your router must return. It is up to you to decide how these parameters are composed.

For both the `PathRouter` and the `MainSubRouter`, parameters are composed from the subsequent parts of the path info string. For example, if the request URL is `https://your.domain/testroute/hello/param1/param2/param3`, the `testroute/hello` route will receive an array of parameters equal to `['param1', 'param2', 'param3']`.

## Identifying the Route

The Core Manager will parse the path info string from the URL called for the request and use it as the first parameter of the `parseRoute(...)` method of your custom router. For example, if the request URL is `https://your.domain/testroute/hello/param1`, the path info string is `testroute/hello/param1`. However, you can decide to use any other strategy at your convenience, like the query string.
