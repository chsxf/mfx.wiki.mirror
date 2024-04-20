The Configuration Manager handles the various [[configuration directives]] you use to control the behavior of MFX.

You can also store your own custom configuration directives in the configuration files and use the Configuration Manager to access them.

## Configuration Files

In the [[Getting Started]] section, we created a basic configuration file.

```php
<?php
use chsxf\MFX\Config;

Config::load([
    'twig' => [
        'templates' => [
            'application/views'
        ]
    ],

    'database' => [
        'servers' => [
            '__default' => [
                'dsn' => 'mysql:dbname=test_mfx;host=localhost',
                'username' => 'your_db_username',
                'password' => 'your_db_password'
            ]
        ]
    ]
]);
```

### Accessing Configuration Directives

Once the configuration is loaded, you can access configuration directives through the following function:

```php
Config::get(string $property, mixed $default = NULL): mixed
```

The `$property` string must be the "dot-separated path" to the property you want to retrieve.

For example, if you want to get the path to the Twig templates, the property is `twig.templates`. Or, to get the password for the `__default` database server, the property would be `databse.servers.__default.password`. In both cases, the function would return a string value.

However, nothing prevents you from retrieving intermediairy properties. For example, the property `database.servers` would return an associative array with a single `__default` key referencing another array with `dsn`, `username` and `password`.

The `$default` parameter is returned if the property you're looking for does not exist in the configuration file.

### Custom Configuration Directives

As states before, you can use your own custom directives in your configuration files. Simply keep in mind that property names can only contain alphanumeric and underscore (`_`) characters.

`my_custom_property` or `My2ndCustomProperty` are valid names.

`my-custom-property` or `my custom property` are not.

### Using Configuration Constants

[[Configuration directives]] provided by MFX can be accessed through constants defined in the `ConfigConstants` class. Each property has its own constant.

For example, to get the path to the Twig templates, you can call `Config::get(ConfigConstants::TWIG_TEMPLATES)`.

## Using Multiple Configuration Files

Every MFX instance should at least have one configuration file. But you can have multiple ones if it better suits your need.

The main configuration file is considered "root domain". It can only be loaded once with the `Config::load()` function.

Additional configuration files may be loaded into other domains by using the following function:

```php
Config::loadOnDomain(string $_domain, string $_path)
```

By calling this function, MFX will load properties contained in the configurationfile located at `$_path` into the domain `$_domain`.

Let's take for example the following configuration file loaded with `Config::loadOnDomain('custom_domain', 'path/to/custom_config.php')`:

```php
<?php
use chsxf\MFX\Config;

Config::load([
    'my_custom_property' => 10
]);
```

To get `my_custom_property`, you would need to call `Config::get('custom_domain.my_custom_property')`. The domain becomes a prefix to any property it contains.

### MFX directives in Sub-domains

If your main configuration file becomes too large for you, you can subdivide it using domains, even for native MFX directives. For example, you could split the example configuration file like this:

```php
// -- This would go in application/config/database.config.php
<?php
use chsxf\MFX\Config;

Config::load([
    'servers' => [
        '__default' => [
            'dsn' => 'mysql:dbname=test_mfx;host=localhost',
            'username' => 'your_db_username',
            'password' => 'your_db_password'
        ]
    ]
]);

// -- This would go in application/config/config.php
<?php
use chsxf\MFX\Config;

Config::load([
    'twig' => [
        'templates' => [
            'application/views'
        ]
    ]
]);

Config::loadOnDomain('database', 'application/config/database.config.php');
```
