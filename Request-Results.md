Instances of the [`RequestResult`](API-RequestResult) class are produced by the routes, and inform the [[Core Manager]] on how it should handle the response to the request. Proceeding this way helps decoupling the business logic to the view offered to the end-user.

## Various Types of Request Results

Request results can be of 5 different types: `VIEW`, `REDIRECT`, `JSON`, `XML`, or `STATUS`. Each type has a very defined use-case we will discuss below.

All request result types can be instanciated with the constructor of the [`RequestResult`](API-RequestResult) class. However, dedicated helpers are provided for some as parameters of the full constructor are not always needed.

Here is the signature of the constructor and a description for each argument:

```php
public function __construct(
    ?RequestResultType $type = NULL,
    mixed $data = NULL,
    ?string $template = NULL,
    ?string $redirectURL = NULL,
    int $statusCode = 200,
    bool $preformatted = false
)
```

| Argument       | Description                                                                                                                                                                                                                                                   |
| -------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `type`         | Type of the request result. If `NULL`, the type becomes `VIEW`.                                                                                                                                                                                               |
| `data`         | For `VIEW` results, it is the data provided to the view template. For `JSON` or `XML` results, it is the data to be serialized. For `STATUS` results, this is the custom message that will override the default message associated with the HTTP status code. |
| `template`     | Name of the Twig template to use. If `NULL`, the template is provided by the route.                                                                                                                                                                           |
| `redirectURL`  | Redirect URL for `REDIRECT` results. If `NULL`, the redirect URL is provided by the route. Ignored for others.                                                                                                                                                |
| `statusCode`   | HTTP status code of the result. For `VIEW` results, if the status code is not equal to 200, the [[Core Manager]] kills the request prematurely. Ignored for `REDIRECT` results.                                                                               |
| `preformatted` | This parameter is ignored for all results but `JSON` and `XML`. If `true`, `data` has already been serialized and will be passed as-is.                                                                                                                       |

### `VIEW` Results

The `VIEW` result type is the most common. This it the result type you use when you want to output some kind of formatted result to the end-user, to the exception of JSON or XML serialized data, which have dedicated result types.

You create a `VIEW` instance of [`RequestResult`](API-RequestResult) thanks to the main constructor. Most of the time, only the `data` argument is filled as the template can be provided by the routes themselves.

### `REDIRECT` Results

The `REDIRECT` result type instructs the [[Core Manager]] to redirect the end-user to a specific URL.

You can create an instance thanks to this helper:

```php
public static function buildRedirectRequestResult(?string $redirectURL = NULL): RequestResult
```

| Argument      | Description                                                                                |
| ------------- | ------------------------------------------------------------------------------------------ |
| `redirectURL` | Redirect URL for `REDIRECT` results. If `NULL`, the redirect URL is provided by the route. |

### `JSON` or `XML` Results

The `JSON` or `XML` result type instructs the [[Core Manager]] to output either JSON or XML data directly to the user, without the need of the template engine.

You can create an instance thanks to these helpers:

```php
public static function buildJSONRequestResult(
    mixed $data,
    bool $preformatted = false,
    int $statusCode = 200
): RequestResult;

public static function buildXMLRequestResult(
    mixed $data,
    bool $preformatted = false,
    int $statusCode = 200
): RequestResult;
```

| Argument       | Description                                                             |
| -------------- | ----------------------------------------------------------------------- |
| `data`         | Data to be serialized. This is generally an array or an object.         |
| `preformatted` | If `true`, `data` has already been serialized and will be passed as-is. |
| `statusCode`   | HTTP status code of the result.                                         |

### `STATUS` Results

The `STATUS` result type instructs the [[Core Manager]] to only output a HTTP status code and an optional custom message.

You can create an instance thanks to this helper:

```php
public static function buildStatusRequestResult(
    int $statusCode = 400,
    ?string $message = NULL
): RequestResult
```

| Argument     | Description                                                                                                                                                          |
| ------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `statusCode` | HTTP status code of the result.                                                                                                                                      |
| `message`    | Custom message that will replace the actual default message associated with HTTP status code. Internally, this is passed to the `data` parameter of the constructor. |

By default, the helper produces a `400 Bad Request` HTTP status response. This has proven very useful to quickly discard invalid incoming requests.
