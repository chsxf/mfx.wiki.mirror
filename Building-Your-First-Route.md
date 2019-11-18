## What is a Route?

Basically, the *route* is the part of the URL that <abbr title="php-micro-framework in short">MFX</abbr> will parse to know what function in your code to call as entry point.

For example, with the following URL:

`https://myfancywebsite.com/Contact.form`

* `https` is the protocol
* `myfancywebsite.com` is the domain name
* `Contact.form` is the route

<abbr title="php-micro-framework in short">MFX</abbr>'s router will then parse `Contact.form` into the **main route** `Contact` and the **sub route** `form`. The main route is then mapped to the `Contact` class and the sub route mapped to the public static `form` function of this class.

For more detailed information on routes, go to the [[Framework Reference]].

## Updating the Configuration

Now we know routes represent a function in a class, we have to tell <abbr title="php-micro-framework in short">MFX</abbr> where to find those classes. To do that, we add options to the configuration file for <abbr title="php-micro-framework in short">MFX</abbr>'s autoloader.

For more information on PHP class autoloading, go to the [official documentation](https://www.php.net/manual/en/language.oop5.autoload.php).

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

Those lines set the `autoload.precedence` configuration option to `app/routes`, telling <abbr title="php-micro-framework in short">MFX</abbr>'s autoloader to look into the `app/routes`folder for classes.

For more detailed information on configuration options, go to the [[Framework Reference]].

## Creating the Route's Class

Let's say we want to create a route called `TestRoute.hello`.

Create a folder named `routes` inside the `app` folder and a file named `TestRoute.php` in it.

**Don't forget to put the `T` and the `R` in uppercase.** <abbr title="php-micro-framework in short">MFX</abbr>'s router is case sensitive.

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

This code includes three mandatory steps:

1. **The `TestRoute` class implements the `IRouteProvider` interface.** This is mandatory for classes to be eligible as main routes.
1. As stated earlier, **sub routes must be public static functions**. So is `hello`.
1. But all public static functions are not suitable for routing. You have to **opt-in functions as sub routes through the `@mfx_subroute` annotation in the doccomment block**.\
   For a deeper explaination of this design concept, you can read [this article on Medium](https://medium.com/@chsxf/php-leveraging-the-reflection-api-to-build-a-simple-request-router-e3efa6fdfb10).

## Final Test

Now go to `http://your.complete.website.url/Test.hello` through your web browser and it should display `Hello, world!`.

Congratulations! You have just completed your very first route.

## Next Step

[[Using Templates]]
