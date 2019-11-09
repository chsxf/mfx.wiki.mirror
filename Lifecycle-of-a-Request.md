## What is a Request?

A request is usually a call to your web server. A remote device issues a request and waits for a response.

## MFX Request Lifecycle

Requests in <abbr title="php-micro-framework in short">MFX</abbr> goes through several stages before a response is provided. Those steps are mostly handled by the [[Core Manager]].

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

If the route path info is invalid and is not a potential match for a missing file, an exception is thrown.

## 3. Calling Pre-processing Callbacks

Before executing routes, two callbacks can be called: the global and the local pre-route callbacks.

As states its name, the global pre-route callback can be defined globally in the config file and is called for every route.

On the other hand, local pre-route callbacks can be defined locally to a route (through the class annotations) and is called only for any contained sub-route.

In both cases, pre-route callbacks are defined as [callables](https://www.php.net/manual/en/language.types.callable.php).

```php
/***
 * @mfx_pre_route_callback MyRouteClass::myPreRouteCallbackMethod
 */
```

By default, no global or local callback is defined.

### Callback Method Signature

Pre-route callback methods must conform to this signature:

```php
myPreRouteCallbackMethod(
	string $_mainRoute,
	string $_subRoute,
	array $_validRouteProviderParameters,
	array $_validSubRouteParameters,
	array $_requestParameters
): void { ... }
```

Argument | Definition
-------- | ----------
$_mainRoute | Name of the called route<br />(`MyRouteClass` in our example)
$_subRoute | Name of the called sub-route<br />(`routeMethod` in our example)
$_validRouteProviderParameters | Route provider parameters based on the route's class annotations
$_validSubRouteParameters | Sub-route parameters based on the route's method annotations
$_requestParameters | Parameters provided with the request<br />(`[ 'param1', 'param2' ]` in our example)

## 4. Pre-Conditions Validation

Some routes may require some pre-conditions to be validated before allowing execution.

At this time, are only supported:
* request method (`POST`, `GET`, `PUT`, ...),
* request content type (`application/json`, `text/html`, ...)

Those pre-conditions requirements are defined in the route's method annotations. Only one request method and content type can be defined for a route's method.

```php
/**
 * @mfx_requires_request_method POST
 * @mfx_requires_content_type application/json
 */
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
	array $_validRouteProviderParameters,
	array $_validSubRouteParameters
): void { ... }
```

Please refer to the [pre-route callback argument list](#callback-method-signature) for further information.
