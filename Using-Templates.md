## Of the Benefits of Templates

In the previous section we created our first route. But that route only produced direct output without any formatting or a proper HTML page structure.

To achieve that, we could modify our `TestRoute.php` as follows:

```php
<?php
use chsxf\MFX\Attributes\SubRoute;
use chsxf\MFX\IRouteProvider;
use chsxf\MFX\RequestResult;

class TestRoute implements IRouteProvider
{
    #[SubRoute]
    public static function hello(): RequestResult {
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

MFX uses Twig as its template engine.

For more information on Twig, go to the [official documentation](https://twig.symfony.com/doc/).

## Setting Templates Root Directory

First, we need to tell MFX where the template files are located. To do that, we will add the `twig.templates` option to the configuration file. For this example, we choose to store our templates files in the `application/views` folder, but you can change it to any value you like.

Open the `application/config/config.php` file and replace the whole content with what follows:

```php
<?php
use chsxf\MFX\Config;

Config::load([
    'autoload' => [
        'precedence' => [
            'application/routes',
        ]
    ],

    'twig' => [
        'templates' => [
            'application/views'
        ]
    ]
]);
```

## Creating the Template File

We want to provide a template file for the `TestRoute.hello` route.

MFX's default behaviour when mapping routes to templates is to complete the templates root folder path with the main route name as a sub folder and the sub route name as the file name.

For the `TestRoute.hello` route, the resulting path will be `application/templates/TestRoute/hello.twig` (with respect of the route's case).

### Updating the Folder Structure

Add a `views` folder to the `application` folder, then a `TestRoute` folder in it.

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
📄 .htaccess
📁 application
  📁 config
    📄 config.php
  📁 routes
    📄 TestRoute.php
  📁 views
    📁 TestRoute
      📄 hello.twig
📄 entrypoint.php
📁 vendor
  📄 autoload.php
  📁 chsxf
  📁 composer
  ... and other things
```

## Adaptating the Route

Now we have created the template file, we have to adapt the route to the new behaviour.

Until now, the route was producing the output directly. In most cases, it is not suitable. Routes should only handle the logic and let MFX and the template engine handle the formatting.

To that extent, routes return instances of the specialized class `RequestResult`. Those objects hold a certain amount of data that can be used by the framework to customize the output.

Open the `application/routes/TestRoute.php` file and replace its content with these lines:

```php
<?php
use chsxf\MFX\Attributes\SubRoute;
use chsxf\MFX\IRouteProvider;
use chsxf\MFX\RequestResult;

class TestRoute implements IRouteProvider
{
    #[SubRoute]
    public static function hello(): RequestResult {
        $templateVars = array(
            'username' => 'stranger'
        );
        return new RequestResult(data: $templateVars);
    }
}
```

First, we create an array containing the template variables to feed the template with. In our case, the `username` variable needs to be provided. Then, the route function returns a `RequestResult` object with the template variables array.

For more information on the `RequestResult` class, go to the [[Framework Reference]].

## Final Test

Now go to `http://your.complete.website.url/Test.hello` through your web browser and it should display `Hello, stranger!` in a properly structured HTML web page.

Congratulations! You have just completed your very first template.

## Next Step

[[Using Databases]]
