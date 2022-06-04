## Assets Management

| Directive     | Description                                                                                                            |            |
| ------------- | ---------------------------------------------------------------------------------------------------------------------- | ---------- |
| `scripts`     | An array of Javascript file URIs to be loaded automatically on every page. This directive supports [[Fake Protocols]]. | _Optional_ |
| `stylesheets` | An array of stylesheet file URIs to be loaded automatically on every page. This directive support [[Fake Protocols]].  | _Optional_ |

### Example

```php
'scripts' => [
    'js://my_script.js', // with a Fake Protocol
    'application/static/scripts/my_other_script.js' // without a Fake Protocol
]
```

## Core Manager

| Directive                | Description                                                                            |            |
| ------------------------ | -------------------------------------------------------------------------------------- | ---------- |
| `mfx_relative_base_href` | Relative path to MFX root folder (defaults to `vendor/chsxf/mfx/static`)               | _Optional_ |
| `base_href`              | Set this directive to override the URI used in the base HTML tag (defaults to `false`) | _Optional_ |

### Requests

| Directive                     | Description                                                                                                                                          |              |
| ----------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ |
| `request.default_route`       | Default route to use if none is provided                                                                                                             | **Required** |
| `request.prefix`              | Prefix to consider when parsing the route from the request. Useful with multi-site setups (defaults to empty string)                                 | _Optional_   |
| `request.pre_route_callback`  | Method (as [callable](https://www.php.net/manual/en/language.types.callable.php)) called just before the route is executed (defaults to `NULL`)      | _Optional_   |
| `request.post_route_callback` | Method (as [callable](https://www.php.net/manual/en/language.types.callable.php)) called just after the route has been executed (defaults to `NULL`) | _Optional_   |

### Responses

| Directive                       | Description                                                                                                                                                  |            |
| ------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------ | ---------- |
| `response.default_content_type` | Content type of the response if none is explicitly specified (defaults to `text/html`)                                                                       | _Optional_ |
| `response.default_charset`      | Charset of the response if none is explicitly specified (defaults to `UTF-8`)                                                                                | _Optional_ |
| `response.full_errors`          | If set to `true`, the error manager will provide error reports with debug information (defaults to `false` - **Not recommended in production environments**) | _Optional_ |

### Routers

| Directive        | Description                                                                                                          |            |
| ---------------- | -------------------------------------------------------------------------------------------------------------------- | ---------- |
| `router.class`   | Class implementing `\chsxf\MFX\Routers\IRouter` to use as the router. Defaults to `\chsxf\MFX\Routers\MainSubRouter` | _Optional_ |
| `router.options` | An associative array describing the options for the specified router. See below the options for the default router   | _Optional_ |

#### Default Router Options

| Directive                          | Description                                                                                                                                   |            |
| ---------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------- | ---------- |
| `allow_default_route_substitution` | If set to `true` and that the request does not respect the route definition pattern, the default route is used in place (defaults to `false`) | _Optional_ |
| `allowed_namespaces`               | List of namespaces in which routes can be found (defaults to no namespace being allowed)                                                      | _Optional_ |

### Example

```php
'request' => [
    'default_route' => 'Home.show',
    'pre_route_callback' => 'Helpers::preRouteCallback'
],
'response' => [
    'default_content_type' => 'application/json',
    'default_charset' => 'ISO-8859-1',
    'full_errors' => true // Not recommended in production environments
],
'router' => [
    'options' => [
        'allow_default_route_substitution' => true,
        'allowed_namespaces' => [
            'fully\\qualified\\namespace',
            'other\\namespace'
        ]
    ]
]
```

## Database Management

| Directive                | Description                                                                                                                                                                                                                                                                                                |            |
| ------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------- |
| `database.error_logging` | If set to `true`, the database manager logs errors in a specific table. For more information, go to the [pdo-database-manager documentation](https://github.com/chsxf/pdo-database-manager#error-logging) (defaults to `false`)                                                                            | _Optional_ |
| `database.servers`       | An associative array where keys are the server names, and the values are the server specific directives. Values as strings are considered name aliases for different server configuration (see Example section). If database management is used, a `__default` server connection is required as a minimum. | _Optional_ |
| `database.updaters`      | An associative array describing the updaters for the database servers                                                                                                                                                                                                                                      | _Optional_ |

### Database Server Specific Directives

MFX uses PDO as a database abstraction layer. See [PDO documentation](https://www.php.net/manual/en/book.pdo.php) for more information on those directives.

| Directive  | Description                     |              |
| ---------- | ------------------------------- | ------------ |
| `dsn`      | Data Source Name for the server | **Required** |
| `username` | Username to access the server   | **Required** |
| `password` | Password to access the server   | **Required** |

### Database Updater Specific Directives

For more information, see the Database Updater documentation.

| Directive | Description                                                       |            |
| --------- | ----------------------------------------------------------------- | ---------- |
| `domain`  | Domain for the updater (defaults to `NULL`)                       | _Optional_ |
| `classes` | An array of classes to load as updaters (defaults to empty array) | _Optional_ |

### Example

```php
'database' => [
    'servers' => [
        '__mfx' => [
            'dsn' => 'mysql:dbname=test_database;host=localhost',
            'username' => 'root',
            'password' => 'root'
        ],
        '__default' => '__mfx' // __default is here an alias of __mfx
    ],
    'updaters' => [
        'domain' => 'main',
        'class' => [
            'MyDatabaseUpdaterClass'
        ]
    ]
]
```

## Fake Protocols

| Directive        | Description                                                                                                                             |            |
| ---------------- | --------------------------------------------------------------------------------------------------------------------------------------- | ---------- |
| `fake_protocols` | An associative array of [[Fake Protocols]] where the key is the name of the protocol, and the value is the path aliased by the protocol | _Optional_ |

### Example

```php
'fake_protocols' => [
    'js' => 'application/static/js',
    'css' => 'application/static/css'
]
```

## Localization (L10n)

| Directive        | Description                                                                                                                                                                                                                                                               |            |
| ---------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------- |
| `default_locale` | Default locale used if the framework is unable to identity the actual locale, or if the actual locale is not supported (defaults to `en_US`)                                                                                                                              | _Optional_ |
| `text_domains`   | An associative array of gettext domains where the key is the name of the domain, and the value is the path to the gettext files. For more information, look for the [`bindtextdomain` function documentation](https://www.php.net/manual/en/function.bindtextdomain.php). | _Optional_ |

### Example

```php
'default_locale' => 'fr_FR',
'text_domains' => [
    '__default' => 'application/messages'
]
```

## Profiler

| Directive   | Description                                                           |            |
| ----------- | --------------------------------------------------------------------- | ---------- |
| `profiling` | If set to `true`, enables the built-in profiler (defaults to `false`) | _Optional_ |

### Example

```php
'profiling' => true // Not recommended in production environments
```

## Session Management

This section allows you to configure PHP session management. For more information, go to [PHP's official documentation](https://www.php.net/manual/en/security.sessions.php).

| Directive             | Description                                                                                        |            |
| --------------------- | -------------------------------------------------------------------------------------------------- | ---------- |
| `session.enabled`     | If set to `true`, PHP session management is enabled. It is disabled otherwise (defaults to `true`) | _Optional_ |
| `session.name`        | PHP session name (defaults to `MFXSESSION`)                                                        | _Optional_ |
| `session.use_cookies` | If set to `true`, PHP will use cookies to maintain session (defaults to `true` - **Recommended**)  | _Optional_ |
| `session.lifetime`    | PHP session duration (defaults to `0`)                                                             | _Optional_ |
| `session.path`        | PHP session path (defaults to website root)                                                        | _Optional_ |
| `session.domain`      | PHP session domain (defaults to empty string)                                                      | _Optional_ |

### Example

```php
'session' => [
    'enabled' => true,
    'name' => 'my_session_name'
]
```

## Templating with Twig

| Directive         | Description                                                                                      |            |
| ----------------- | ------------------------------------------------------------------------------------------------ | ---------- |
| `twig.templates`  | An array of paths when looking for template files (defaults to empty array)                      | _Optional_ |
| `twig.cache`      | Path of the template cache directory, or `false` to disable cache (defaults to `tmp/twig_cache`) | _Optional_ |
| `twig.extensions` | An array of extension class names for Twig to load (defaults to empty array)                     | _Optional_ |

### Example

```php
'twig' => [
    'cache' => false, // Not recommended for production environments
    'templates' => [
        'application/templates'
    ],
    'extensions' => [
        'MyTwigExtensionClass'
    ]
]
```

## Timezone Management

| Directive  | Description                                                                                                                                                                                                      |            |
| ---------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------- |
| `timezone` | Sets the timezone for the server (defaults to `UTC`). For more information, go to the [`date_default_timezone_set` function documentation](https://www.php.net/manual/en/function.date-default-timezone-set.php) | _Optional_ |

### Example

```php
'timezone' => 'Europe/Paris'
```

## User Management

| Directive                   | Description                                                                              |            |
| --------------------------- | ---------------------------------------------------------------------------------------- | ---------- |
| `user_management.class`     | Set this directive to override the user management class (defaults to `\chsxf\MFX\User`) | _Optional_ |
| `user_management.key_field` | Name of the key field in users database table (defaults to `user_id`)                    | _Optional_ |
| `user_management.table`     | Name of the users database table (defaults to `mfx_users`)                               | _Optional_ |

### Example

```php
'user_management' => [
    'class' => 'MyUserClass',
    'key_field' => 'id',
    'table' => 'users'
]
```
