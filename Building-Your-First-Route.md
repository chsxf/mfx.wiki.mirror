## What is a Route?

Basically, the *route* is the part of the URL that MFX will parse to know what function in your code to call as entry point.

For example, with the following URL:

`https://myfancywebsite.com/Contact.form`

* `https` is the protocol
* `myfancywebsite.com` is the domain name
* `Contact.form` is the route

MFX's router will then parse `Contact.form` into the **main route** `Contact` and the **sub route** `form`. The main route is then mapped to the `Contact` class and the sub route mapped to the public static `form` function of this class.

For more detailed information on routes, go to the [[Framework Reference]].

## Updating the Configuration

Now we know routes represent a function in a class, we have to tell MFX where to find those classes. To do that, we add options to the configuration file for MFX's autoloader. For more information on PHP class autoloading, go to the [official documentation](https://www.php.net/manual/en/language.oop5.autoload.php).

Open the `app/config/config.php` file and replace the whole content with what follows:

```php
<?php
\CheeseBurgames\MFX\Config::load(array(
		'autoload' => array(
				'precedence' => array(
						'app/routes'
				)
		)
));
```

Those lines set the `autoload.precedence` configuration option to `app/routes`, telling MFX's autoloader to look into the `app/routes`folder for classes.

For more detailed information on configuration options, go to the [[Framework Reference]].

## Creating the Route's Class

Create a folder named `routes` inside the `app` folder and a file named `TestRoute.php` in it.

**Don't forget to put the `T` and the `R` in uppercase.** MFX's router is case sensitive.

At this point, your repository should look like this:

```
📁 .git
📄 .gitmodules
📄 .htaccess
📁 app
  📁 config
    📄 config.php
  📁 routes
    📄 TestRoute.php
📄 entrypoint.php
📁 mfx
```

Then, open the `TestRoute.php` file and paste these lines in it:

```php
<?php
use \CheeseBurgames\MFX\IRouteProvider;

class TestRoute implements IRouteProvider {

	/**
	 * @mfx_subroute
	 */
	public static function hello() {
		echo 'Hello, world!';
		exit();
	}

}
```

## Next Step

[[Bla bla]]
