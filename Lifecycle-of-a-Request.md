## What is a Request?

A request is usually a call to your web server. A remote device issues a request and waits for a response.

## Request Lifecycle

Requests in MFX goes through several stages before a response is provided. These steps are mostly handled by the [[Core Manager]].

1. Route path info extraction from the request URL
1. Route path info parsing and validation
1. Calling pre-processing callbacks
1. Pre-conditions validation
1. Processing the route
1. Calling post-processing callbacks

We go into further details in the following sections.

## 1. Route Path Info Extraction From the Request URL

For example, with the URL being `https://my.web.server/MyRouteClass.routeMethod`, the route path info is `MyRouteClass.routeMethod`.

If route path info is empty, the default route is used instead. In case the default route has been set to `none`, MFX immediately ends the process with a `HTTP 200 OK` status code.

## 2. Route Path Info Parsing and Validation

Once the route path info has been extracted from the request URL, it is now time to parse and validate it.

Depending on the router you are using, the form of your route path info may differ. For example, with the [`MainSubRouter`](API-Routers-MainSubRouter), a valid route path info must conform to the regular expression: `/^[[:alnum:]_]+\.[[:alnum:]_]+?$/` and match existing class and method. But with the [`PathRouter`](API-Routers-PathRouter), a valid route path info must conform to the regular expression: `#^[[:alnum:]_]+/[[:alnum:]_]+?$#`.

If the route path info is invalid and is not a potential match for an actual existing file, an exception is thrown.

### Arguments

Depending on the router your are using, the route path info may contain additional parameters that you can pass to the route, in complement of regular global arrays like `$_GET` or `$_POST`.

For example, with the [`MainSubRouter`](API-Routers-MainSubRouter) and the URL `https://my.web.server/MyRouteClass.routeMethod/param1/param2`, route arguments will be `['param1', 'param2']`.

## 3. Calling Pre-processing Callbacks

Before executing routes, three pre-route callbacks can be called: one global, one local to the route provider, and one local to the route itself. You can use these callbacks to implement custom validations outside of MFX's built-in lifecycle and end requests prematurely if needed.

As states its name, the global pre-route callback can be defined globally in the config file and is called for every route.

```php
Config::load([
    // ...
    'request' => [
        // ...
        'pre_route_callback' => 'MyRouteClass::myPreRouteCallbackMethod'
    ],
    // ...
]);
```

On the other hand, local pre-route callbacks can be defined locally to a route or a route provider (thanks to the `PreRouteCallback` attribute) and are called only for the corresponding route or route provider.

All three types of pre-route callbacks can be defined at the same time and are executed sequentially (global, then local to the route provider, then local to the route).

In all cases, pre-route callbacks are defined as [callables](https://www.php.net/manual/en/language.types.callable.php).

```php
#[PreRouteCallback('MyRouteClass::myPreRouteCallbackMethod')]
```

By default, no global or local callback is defined.

### Callback Method Signature

Pre-route callback methods must conform to this signature:

```php
function myPreRouteCallbackMethod(RouterData $_routerData): void { /* ... */ }
```

Look at the `RouterData` class documentation for more information.

## 4. Pre-Conditions Validation

Some routes may require some pre-conditions to be validated before allowing execution.

At this time, are only supported:

- request method (`POST`, `GET`, `PUT`, ...),
- request content type (`application/json`, `text/html`, ...)

These pre-condition requirements are defined in the route's method annotations. Only one request method and content type can be defined for a route's method.

```php
#[RequiredRequestMethod('POST')]
#[RequiredContentType('application/json')]
```

If any of the pre-conditions is not met, the request ends with an HTTP error code (`405 Method Not Allowed` for the request method or `415 Unsupported Media Type` for the content type).

## 5. Processing the Route

Once everything has been validated, the route is called and a [`RequestResult`](API-RequestResult) object is obtained. Subsequent behaviour depends on the type of result for the request (among `VIEW`, `REDIRECT`, `JSON`, `XML`, `STATUS`).

| Type of Result | Behaviour                                                          |
| -------------- | ------------------------------------------------------------------ |
| VIEW           | A view based on a Twig template is generated                       |
| REDIRECT       | A location header is generated to redirect the request             |
| JSON or XML    | The [request result](Request-Results) is serialized as JSON or XML |
| STATUS         | A HTTP status code is generated without any other output           |

## 6. Calling Post-processing Callbacks

After having executed the route, post-route callbacks, similar to the pre-route callbacks, can be executed. However, they are executed in reverse order (local to the route first, then local to the route provider, then global).

As the pre-route callbacks, the post-route callback method must conform to this signature:

```php
function myPostRouteCallbackMethod(RouterData $_routerData): void { /* ... */ }
```

Look at the `RouterData` class documentation for more information.
