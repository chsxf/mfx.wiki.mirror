## What is a Route?

Basically, the *route path* is the part of the URL that MFX will parse to know what function in your code to call as entry point.

For example, if using the default router with the following URL:

`https://myfancywebsite.com/Contact.form`

* `https` is the protocol
* `myfancywebsite.com` is the domain name
* `Contact.form` is the route path

MFX's default router will then parse `Contact.form` into the **route provider** `Contact` and the **route** `form`. The route provider is then mapped to the `Contact` class and the route to the `form` public static function of this class.

For more detailed information on routes or routeurs, go to the [[Framework Reference]].

## Updating the Configuration

Now we know routes represent a function in a class, we have to tell MFX where to find those classes. To do that, we have to modify the `composer.json` file.

For more information on PHP and Composer class autoloading, go to the [official PHP documentation](https://www.php.net/manual/en/language.oop5.autoload.php) and to the [Composer documentation](https://getcomposer.org/doc/01-basic-usage.md#autoloading).

Open the `composer.json` file and add the `autoload` directive as follows:

```json
"autoload": {
  "psr-4": {
    "": "application/routes"
  }
}
```

Those lines add the `application/routes` folder to the autoload process, informing MFX to look into the `application/routes`folder for classes.

Run the following command to update your website configuration:

```
composer update
```

## Creating the Route's Class

Let's say we want to create a route called `TestRoute.hello`.

Create a folder named `routes` inside the `application` folder and a file named `TestRoute.php` in it.

**Don't forget to put the `T` and the `R` in uppercase.** MFX's default router is case sensitive.

At this point, your repository should look like this:

```
📁 .git
📄 .htaccess
📁 application
  📁 config
    📄 config.php
  📁 routes
    📄 TestRoute.php
📄 entrypoint.php
📁 vendor
  📄 autoload.php
  📁 chsxf
  📁 composer
  ... and other things
```

Then, open `TestRoute.php` and paste these lines in it:

```php
<?php
use chsxf\MFX\Attributes\Route;
use chsxf\MFX\Routers\IRouteProvider;
use chsxf\MFX\RequestResult;

class TestRoute implements IRouteProvider
{
    #[Route]
    public static function hello(): RequestResult {
        echo 'Hello, world!';
        exit();
    }
}
```

This code includes three mandatory steps:

1. **The `TestRoute` class implements the `IRouteProvider` interface.** This is mandatory for classes to be eligible as route providers.
2. As stated earlier, **routes must be public static functions**. So is `hello`.
3. But all public static functions are not suitable for routing. You have to **opt-in functions as routes through the `#[Route]` attribute**.

## Final Test

Now go to `http://your.complete.website.url/Test.hello` through your web browser and it should display `Hello, world!`.

Congratulations! You have just completed your very first route.

## Next Step

[[Using Templates]]
