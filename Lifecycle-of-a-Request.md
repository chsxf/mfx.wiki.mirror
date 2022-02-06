## What is a Request?

A request is usually a call to your web server. A remote device issues a request and waits for a response.

## MFX Request Lifecycle

Requests in MFX goes through several stages before a response is provided. Those steps are mostly handled by the [[Core Manager]].

1. Route path info extraction from the request URI  
1. Route path info validation
1. Calling pre-processing callbacks
1. Pre-conditions validation
1. Processing the route
1. Calling post-processing callbacks

We go into further details in the following sections.

## 1. Route Path Info Extraction From the Request URI  

For example, with the URI being `https://my.web.server/MyRouteClass.routeMethod`, route path info is `MyRouteClass.routeMethod`.

### The Request URI Does Not Hold Route Path Info

If route path info is empty, the default route is used instead.

In case the default route has been set to `none`, MFX immediately ends the process with a `HTTP 200 OK` status code.

### Route Path Info With Several Element

In case of the route path info has more than one element (ie `MyRouteClass.routeMethod/param1/param2`), the first element is kept as the route path info and subsequent elements are extracted as parameters.
* `MyRouteClass.routeMethod` remains route path info,
* `param1` and `param2` become parameters for the route

## 2. Route Path Info Validation

Once the route path info has been extracted from the request URI, it is now time to validate it.

A valid route path info must conform to the regular expression: `/^[[:alnum:]_]+\.[[:alnum:]_]+?$/` and match existing class and method.

If the route path info is invalid and is not a potential match for an actual existing file, an exception is thrown.

## 3. Calling Pre-processing Callbacks

Before executing routes, three callbacks can be called: the global and the local pre-route callbacks. You can use those callbacks to implement custom validations outside of MFX's built-in lifecycle and end requests prematurely if needed.

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

On the other hand, local pre-route callbacks can be defined locally to a route or a sub route (thanks to the `PreRouteCallback` attribute) and are called only for the corresponding route or sub-route.

All three types of pre-route callbacks can be defined at the same time and are executed sequentially (global, then route, then subroute).

In all cases, pre-route callbacks are defined as [callables](https://www.php.net/manual/en/language.types.callable.php).

```php
#[PreRouteCallback('MyRouteClass::myPreRouteCallbackMethod')]
```

By default, no global or local callback is defined.

### Callback Method Signature

Pre-route callback methods must conform to this signature:

```php
myPreRouteCallbackMethod(
    string $_mainRoute,
    string $_subRoute,
    RouteAttributesParser $_routeAttributeParser,
    RouteAttributesParser $_subRouteAttributesParser,
    array $_requestParameters
): void { /* ... */ }
```

Argument | Definition
-------- | ----------
$_mainRoute | Name of the called route<br />(`MyRouteClass` in our example)
$_subRoute | Name of the called sub-route<br />(`routeMethod` in our example)
$_routeAttributeParser | Route attributes parser based on the route's class attributes
$_subRouteAttributesParser | Sub-route attributes parser based on the route's method attributes
$_requestParameters | Parameters provided with the request<br />(`[ 'param1', 'param2' ]` in our example)

## 4. Pre-Conditions Validation

Some routes may require some pre-conditions to be validated before allowing execution.

At this time, are only supported:
* request method (`POST`, `GET`, `PUT`, ...),
* request content type (`application/json`, `text/html`, ...)

Those pre-conditions requirements are defined in the route's method annotations. Only one request method and content type can be defined for a route's method.

```php
#[RequiredRequestMethod('POST')]
#[RequiredContentType('application/json')]
```

If any of the pre-condition is not met, the request ends with an HTTP error code (`405 Method Not Allowed` for the request method or `415 Unsupported Media Type` for the content type).

## 5. Processing the Route

Once everything has been validated, the route is called and a `RequestResult` object is obtained. Subsequent behaviour depends on the type of result for the request (among `VIEW`, `REDIRECT`, `JSON`, `XML`, `STATUS`).

Type of Result | Behaviour
-------------- | ---------
VIEW | A view based on a Twig template is generated
REDIRECT | A location header is generated to redirect the request
JSON or XML | The request result is serialized as JSON or XML
STATUS | A HTTP status code is generated without any other output

## 6. Calling Post-processing Callbacks

After having executed the route, a post-route callback similar to the pre-route callbacks can be executed. However, only a global post-route callback can be defined.

The post-route callback method must conform to this signature:

```php
myPostRouteCallbackMethod(
    string $_mainRoute,
    string $_subRoute,
    RouteAttributesParser $_routeAttributesParser,
    RouteAttributesParser $_subRouteAttributesParser
): void { /* ... */ }
```

Please refer to the [pre-route callback argument list](#callback-method-signature) for further information.
