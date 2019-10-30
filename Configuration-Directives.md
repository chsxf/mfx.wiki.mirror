### Assets Management

Directive | Description | -
--------- | ----------- | -
`scripts` | An array of Javascript file URIs to be loaded automatically on every page. This directive supports [[Fake Protocols]]. | *Optional*
`stylesheets` | An array of stylesheet file URIs to be loaded automatically on every page. This directive support [[Fake Protocols]]. | *Optional*

#### Example

```php
'scripts' => array(
	'js://my_script.js', // with a Fake Protocol
	'app/static/scripts/my_other_script.js' // without a Fake Protocol
)
```

### Autoloading

Directive | Description | -
--------- | ----------- | -
`autoload.precedence` | An array of folders into which the autoloader will look for. The autoloaded elements will be looked in order of precedence in that list. That list is however always prepend with <abbr title="php-micro-framework in short">MFX</abbr>'s own folders. Thus, it is not possible to override one of the framework's classes with a custom one. | *Optional*

#### Example

```php
'autoload' => array(
	'precedence' => array(
		'app/classes',
		'app/interfaces'
	)
)
```

### Core Manager

Directive | Description | -
--------- | ----------- | -
`mfx_relative_base_href` | Relative path to MFX root folder (defaults to `mfx`) | *Optional*
`allow_default_route_substitution` | If set to `true` and that the request does not respect the route definition pattern, the default route is used in place (defaults to `true`) | *Optional*
`base_href` | Set this directive to override the URI used in the base HTML tag (defaults to `false`) | *Optional*

#### Requests

Directive | Description | -
--------- | ----------- | -
`request.default_route` | Defaults route to use if none is provided | **Required**
`request.prefix` | Prefix to consider when parsing the route from the request. Useful with multi-site setups (defaults to empty string) | *Optional*
`request.pre_route_callback` | Method (as [callable](https://www.php.net/manual/en/language.types.callable.php)) called just before the route is executed (defaults to `NULL`) | *Optional*
`request.post_route_callback` | Method (as [callable](https://www.php.net/manual/en/language.types.callable.php)) called just after the route has been executed (defaults to `NULL`) | *Optional*

#### Responses

Directive | Description | -
--------- | ----------- | -
`response.default_content_type` | Content type of the response if none is explicitly specified (defaults to `text/html`) | *Optional*
`response.default_charset` | Charset of the response if none is explicitly specified (defaults to `UTF-8`) | *Optional*
`response.full_errors` | If set to `true`, the error manager will provide error reports will debug information (defaults to `false`) | *Optional*

#### Example

```php
'allow_default_route_substitution' => true,
'request' => array(
	'default_route' => 'Home.show',
	'pre_route_callback' => array( 'Helpers', 'preRouteCallback' )
),
'response' => array(
	'default_content_type' => 'application/json',
	'default_charset' => 'ISO-8859-1',
	'full_errors' => true // Not recommended in production environments
)
```

### Database Management

Directive | Description | -
--------- | ----------- | -
`database.error_logging` | If set to `true`, the database manager logs errors in a specific table. For more information, go to the [pdo-database-manager documentation](https://github.com/cheeseburgames/pdo-database-manager) (defaults to `false`) | *Optional*
`database.servers` | An associative array where keys are the server names, and the values are the server specific directives. Values as strings are considered name aliases for different server configuration (see Example section). If database management is used, a `__default` server connection is required as a minimum. | *Optional*
`database.updaters` | An array of updaters for the database servers | *Optional*

#### Database Server Specific Directives

<abbr title="php-micro-framework in short">MFX</abbr> uses PDO as a database abstraction layer. See [PDO documentation](https://www.php.net/manual/en/book.pdo.php) for more information on those directives.

Directive | Description | -
--------- | ----------- | -
`dsn` | Data Source Name for the server | **Required**
`username` | Username to access the server | **Required**
`password` | Password to access the server | **Required**

#### Database Updater Specific Directives

For more information, see the Database Updater documentation.

Directive | Description | -
--------- | ----------- | -
`domain` | Domain for the updater (defaults to `NULL`) | *Optional*
`classes` | An array of classes to load as updaters (defaults to empty array) | *Optional*

#### Example

```php
'database' => array(
	'servers' => array(
		'__mfx' => array(
			'dsn' => 'mysql:dbname=test_database;host=localhost',
			'username' => 'root',
			'password' => 'root'
		),
		'__default' => '__mfx' // __default is here an alias of __mfx
	),
	'updaters' => array(
		'domain' => 'main',
		'class' => array(
			'MyDatabaseUpdaterClass'
		)
	)
)
```

### Documentation Comment Parser

Directive | Description | -
--------- | ----------- | -
`doccommentparser.class` | Set this directive to override the documentation comment parser (defaults to empty string) | *Optional*
`doccommentparser.prefixes` | An array of prefixes to consider valid when parsing documentation comments (defaults to empty array) | *Optional*

#### Example

```php
'doccommentparser' => array(,
	'class' => 'MyDocCommentParserClass',
	'prefixes' => array(
		'backoffice_'
	)
)
```

### Fake Protocols

Directive | Description | -
--------- | ----------- | -
`fake_protocols` | An associative array of [[Fake Protocols]] where the key is the name of the protocol, and the value is the path aliased by the protocol | *Optional*

#### Example

```php
'fake_protocols' => array(
	'js' => 'app/static/js',
	'css' => 'app/static/css'
)
```

### Localization (L10n)

Directive | Description | -
--------- | ----------- | -
`default_locale` | Default locale used if the framework is unable to identity the actual locale, or if the actual locale is not supported (defaults to `en_US`) | *Optional*
`text_domains` | An associative array of gettext domains where the key is the name of the domain, and the value is the path to the gettext files. For more information, look for the [`bindtextdomain` function documentation](https://www.php.net/manual/en/function.bindtextdomain.php). | *Optional*

#### Example

```php
'text_domains' => array(
	'__default' => 'app/messages'
)
```

### Profiler

Directive | Description | -
--------- | ----------- | -
`profiling` | If set to `true`, enables the built-in profiler (defaults to `false`) | *Optional*

#### Example

```php
'profiling' => true // Not recommended in production environments
```

### Session Management

This section allows you to configure PHP session management. For more information, go to the [official documentation](https://www.php.net/manual/en/security.sessions.php).

Directive | Description | -
--------- | ----------- | -
`session.enabled` | If set to `true`, PHP session management is enabled. It is disabled otherwise (default to `true`) | *Optional*
`session.name` | PHP session name (defaults to `MFXSESSION`) | *Optional*
`session.use_cookies` | If set to `true`, PHP will use cookies to maintain session (defaults to `true` - recommended) | *Optional*
`session.lifetime` | PHP session duration (defaults to `0`) | *Optional*
`session.path` | PHP session path (defaults to website root) | *Optional*
`session.domain` | PHP session domain (defaults to empty string) | *Optional*

#### Example

```php
'session' => array(
	'enabled' => true,
	'name' => 'my_session_name'
)
```

### Templating with Twig

Directive | Description | -
--------- | ----------- | -
`twig.templates` | An array of paths when looking for template files (defaults to empty array) | *Optional*
`twig.cache` | Path of the template cache directory, or `false` to disable cache (defaults to `tmp/twig_cache`) | *Optional*
`twig.extensions` | An array of extension class names for Twig to load (defaults to empty array) | *Optional*

#### Example

```php
'twig' => array(
	'cache' => false, // Not recommended for production environments
	'templates' => array(
		'app/templates'
	),
	'extensions' => array(
		'MyTwigExtensionClass'
	)
)
```

### Timezone Management

Directive | Description | -
--------- | ----------- | -
`timezone` | Sets the timezone for the server (defaults to `UTC`). For more information, go to the [`date_default_timezone_set` function documentation](https://www.php.net/manual/en/function.date-default-timezone-set.php) | *Optional* 

#### Example

```php
'timezone' => 'Europe/Paris'
```

### User Management

Directive | Description | -
--------- | ----------- | -
`user_management.class` | Set this directive to override the user management class (defaults to `\CheeseBurgames\MFX\User`) | *Optional*
`user_management.key_field` | Name of the key field in users database table (defaults to `user_id`) | *Optional* 
`user_management.table` | Name of the users database table (defaults to `mfx_users`) | *Optional*

#### Example

```php
'user_management' => array(
	'class' => 'MyUserClass',
	'key_field' => 'id',
	'table' => 'users'
)
```
