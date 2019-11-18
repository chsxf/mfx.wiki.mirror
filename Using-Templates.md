## Of the Benefits of Templates

In the previous section we created our first route. But that route only produced direct output without any formatting or a proper HTML page structure.

To achieve that, we could do this:

```php
<?php
use \CheeseBurgames\MFX\IRouteProvider;

class TestRoute implements IRouteProvider {

	/**
	 * @mfx_subroute
	 */
	public static function hello() {
?>
<!DOCTYPE html>
<html>
<head>
	<title>Hello, world!</title>
</head>
<body>
	<p>Hello, world!</p>
</body>
</html>
<?php
		exit();
	}

}
```

... But it would rapidly become impractical in a real production situation.

### Here Come Templates

Templates allow you to separate your logic from your presentation. This way, the routes handle logic and feed the templates with what they want to present to the user.

<abbr title="php-micro-framework in short">MFX</abbr> uses Twig as its template engine.

For more information on Twig, go to the [official documentation](https://twig.symfony.com/doc/1.x/).\
*(Be sure to use Twig 1.x docs as <abbr title="php-micro-framework in short">MFX</abbr> is not compatible with Twig 2.x yet)*

## Setting Templates Root Directory

First, we need to tell <abbr title="php-micro-framework in short">MFX</abbr> where the template files are located. To do that, we will add the `twig.templates` option to the configuration file. For this example, we choose to store our templates files in the `app/templates` folder, but you can change it to any value you like.

Open the `app/config/config.php` file and replace the whole content with what follows:

```php
<?php
\CheeseBurgames\MFX\Config::load(array(
	'autoload' => array(
		'precedence' => array(
			'app/routes'
		)
	),

	'twig' => array(
		'templates' => array(
			'app/templates'
		)
	)
));
```

## Creating the Template File

We want to provide a template file for the `TestRoute.hello` route.

<abbr title="php-micro-framework in short">MFX</abbr>'s default behaviour when mapping routes to templates is to complete the templates root folder path with the class name as a sub folder and the method name as the file name.

For `TestRoute.hello`, the resulting path will be `app/templates/TestRoute/hello.twig` (with respect of the route's case).

### Updating the Folder Structure

Add a `templates` folder to the `app` folder, then a `TestRoute` folder in the new folder.

After that, we have to create a `hello.twig` file and paste these lines in it:

```twig
{% extends "@mfx/HTML.twig" %}

{% block body %}
	{{ parent() }}

	<p>Hello, {{ username }}!</p>
{% endblock %}
```

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
  📁 templates
    📁 TestRoute
      📄 hello.twig
📄 entrypoint.php
📁 mfx
```

## Adaptating the Route

Now we have created the template file, we have to adapt the route to the new behaviour.

Until now, the route was producing the output directly. In most cases, it is not suitable. Routes should only handle the logic and let <abbr title="php-micro-framework in short">MFX</abbr> and the template engine handle the formatting.

To that extent, routes return instances of the specialized class `RequestResult`. Those objects hold a certain amount of data that can be used by the framework to customize the output.

Open the `app/routes/TestRoute.php` file and replace its content with these lines:

```php
<?php
use CheeseBurgames\MFX\IRouteProvider;
use CheeseBurgames\MFX\RequestResult;

class TestRoute implements IRouteProvider {

	/**
	 * @mfx_subroute
	 */
	public static function hello() {
		$templateVars = array(
				'username' => 'stranger'
		);
		return new RequestResult(NULL, $templateVars);
	}

}
```

First, we create an array containing the template variables to feed the template with. In our case, the `username` variable needs to be provided. Then, the route function returns a `RequestResult` object with `NULL` and the template variables array. `NULL` is passed as the first argument to tell <abbr title="php-micro-framework in short">MFX</abbr> to generate automatically the template file path from the route name.

For more information on the `RequestResult` class, go to the [[Framework Reference]].

## Conclusion

You are now ready to continue your journey the framework. Go to the [[Framework Reference]] to get a deeper look into <abbr title="php-micro-framework in short">MFX</abbr>.
