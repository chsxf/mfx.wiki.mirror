## Introduction to Databases With MFX

Database management with MFX is fairly simple. MFX uses [PDO](https://www.php.net/manual/en/book.pdo.php) through an extended class provided by the [pdo-database-manager](https://github.com/chsxf/pdo-database-manager) package.

By using PDO, we ensure MFX to be compatible pretty much out-of-the-box with every database management system supported by this abstraction layer.

## Creating a Database

Launch your database server and create a database called `test_mfx`, then execute the following SQL instructions for the example to run properly.

```sql
CREATE TABLE `users` (
    `id` INT UNSIGNED NOT NULL AUTO_INCREMENT,
    `username` VARCHAR(255) NOT NULL,
    PRIMARY KEY (`id`)
);

INSERT INTO `users` (`id`, `username`) VALUES
    (NULL, 'sponge_bob'),
    (NULL, 'aragorn'),
    (NULL, 'bart_simpson'),
    (NULL, 'mickey_mouse');
```

## Updating the Configuration

The first step to bring database support into your app is to update your configuration file.

Open the `application/config/config.php` file and replace the whole content with what follows. Be sure to replace `your_db_username` and `your_db_password` with the credentials for your database. You may also need to adjust the `dsn` option to fit your needs.

```php
<?php
use chsxf\MFX\Config;

Config::load([
    'twig' => [
        'templates' => [
            'views'
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

## Updating the Route

Now, we are all set up, we will be able to use the database and the table we created.

In this example, we will pick a random user from the database and display its username with the template we wrote in the previous step.

Open the `application/routes/TestRoute.php` file replace the whole content with what follows:

```php
<?php
use chsxf\MFX\Attributes\Route;
use chsxf\MFX\Routers\IRouteProvider;
use chsxf\MFX\RequestResult;

class TestRoute implements IRouteProvider
{
    #[Route]
    public static function hello(): RequestResult {
        $dbm = DatabaseManager::open();

        $sql = "SELECT * FROM `users` ORDER BY RAND() LIMIT 1";
        $row = $dbm->getRow($sql, \PDO::FETCH_ASSOC);

        $templateVars = $row;
        return new RequestResult(data: $templateVars);
    }
}
```

### Details

- First, we open a connection to the database server with the `DatabaseManager::open()` function. It uses the `__default` server configuration options as no server name is provided,
- Then, we execute our query with the `getRow()` method and ask the result to be provided as an associative array (the `getRow()` method is an extension method provided by the [pdo-database-manager](https://packagist.org/packages/chsxf/pdo-database-manager) package),
- Finally, we pass the result as the template variables to display the selected user's name.

If everything works fine, you should get this kind of result on screen:

```
Hello, mickey_mouse!
```

## Conclusion

You are now ready to continue your journey with the framework. Go to the [[Framework Reference]] to get a deeper look into MFX.
