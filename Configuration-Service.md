The Configuration Service handles the various [[configuration directives]] you use to control the behavior of MFX.

You can also store your own custom configuration directives in the configuration files and use the Configuration Service to access them.

The Configuration Service implements the `IConfigService` interface.

## Configuration Files

In the [[Getting Started]] section, we created a basic configuration file.

```php
<?php
use chsxf\MFX\Config;

return new Config([
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

Once the configuration is loaded, you can access configuration directives through the following functions:

```php
function getValue(string $property, mixed $default = null, ?string $domain = null): mixed;

function tryGetValue(string $property, mixed &$outValue, ?string $domain = null): bool;
```

The `$property` string must be the "dot-separated path" to the property you want to retrieve.

For example, if you want to get the path to the Twig templates, the property is `twig.templates`. Or, to get the password for the `__default` database server, the property would be `databse.servers.__default.password`. In both cases, the function would return a string value.

However, nothing prevents you from retrieving intermediary properties. For example, the property `database.servers` would return an associative array with a single `__default` key referencing another array with `dsn`, `username` and `password`.

In `getValue`, the `$default` parameter is returned if the property you're looking for does not exist in the configuration file. On the other hand, if the property exists `tryGetValue` will set `$outValue` to the property's value and return `true`, or `false` otherwise.

By default, both functions works on the default domain.

### Custom Configuration Directives

As stated before, you can use your own custom directives in your configuration files. Simply keep in mind that property names can only contain alphanumeric and underscore (`_`) characters.

`my_custom_property` or `My2ndCustomProperty` are valid names.

`my-custom-property` or `my custom property` are not.

### Using Configuration Constants

[[Configuration directives]] provided by MFX can be accessed through constants defined in the `ConfigConstants` class. Each property has its own constant.

For example, to get the path to the Twig templates, you can call `getValue(ConfigConstants::TWIG_TEMPLATES)`.

## Using Multiple Configuration Files

Every MFX instance must have at least one configuration file. But you can have multiple ones if it better suits your need.

The main configuration file is considered "root domain" or "default domain". It is loaded first when initializing MFX.

Additional configuration files may be loaded into other domains by using the following function:

```php
function load(Config $configData, string $domain = self::DEFAULT_DOMAIN);
```

By calling this function, MFX will load properties contained in `$configData` into the domain `$domain`.

### Example

```php
// config/custom-config.php
<?php
use chsxf\MFX\Config;

return new Config([
    'my_custom_property' => 10
]);

// In a callback or route somewhere else
// ...
$configData = require_once('config/custom-config.php');
$configService = $this->serviceProvider->getConfigService();
$configService->load($configData, 'custom_domain');
```

To get `my_custom_property`, you would need to call `getValue('my_custom_property', 'custom_domain')` or `getValue('custom_domain.my_custom_property')`. The domain can be used as a prefix to any property it contains.

### MFX directives in Sub-domains

If your main configuration file becomes too large for you, you can subdivide it using domains, even for native MFX directives. For example, you could split the example configuration file like this:

```php
// This would go in config/database.config.php
<?php
use chsxf\MFX\Config;

return new Config([
    'servers' => [
        '__default' => [
            'dsn' => 'mysql:dbname=test_mfx;host=localhost',
            'username' => 'your_db_username',
            'password' => 'your_db_password'
        ]
    ]
]);

// This would go in config/config.php
<?php
use chsxf\MFX\Config;

return new Config([
    'twig' => [
        'templates' => [
            'views'
        ]
    ]
]);

// Somewhere else
$databaseConfigData = require_once('config/database.config.php');
$configService = $this->serviceProvider->getConfigService();
$configService->load($databaseConfigData, 'database');
```
