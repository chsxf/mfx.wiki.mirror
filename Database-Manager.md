The Database Manager provides a simple way to handle database connections.

Even if most users will only need a single database connection, MFX allows for several in the [configuration directives](Configuration-Directives#database-management). And the Database Manager is here to handle opening, reusing and closing these connections.

The `DatabaseManager` class inherits from the class of the same name in the [`pdo-database-manager`](https://github.com/chsxf/pdo-database-manager) package, and comes with all the same benefits (helpers improving query management, error logging, ...). Please refer to the [corresponding documenation](https://github.com/chsxf/pdo-database-manager) for more information.

## Opening a Connection

Use this method to open a connection:

```php
DatabaseManager::open(string $server = '__default', bool $forceNew = false): DatabaseManager
```

By default, without any parameter, the Database Manager will try to open the database connection referenced as `__default` in the configuration or reuse a previously opened connection if such exists. For this call to work, a `__default` connection must exist in your configuration file.

However, you can provide any other existing connection name for the `$server` parameter to open or reuse an existing connection object to another database.

If `$forceNew` is set to `true`, the Database Manager will try to open a new connection to the database even if another opened connection already exists.

The function returns the requested connection instance, or throws a `chsxf\PDO\DatabaseManagerException` if an error occurs.

## Closing a Connection

As any other PHP processes that do not use persistant connections to database servers, MFX will close all database connections at the end of each request.

Howerver by using the connection instances returned by `open`, you can explictly close a connection at any moment. Database instances being heavily used for most requests of a website or API, it is important to preserve them as much as possible. So you may want to cut connections as soon as possible, especially if you have long processes after your database queries have finished.

To close a connection, just call the following method:

```php
DatabaseManager::close(DatabaseManager &$_manager)
```

_Note: Unsetting the connection instance is not enough to close a connection as the Database Manager keeps track of all opened connection to be able to reuse them if needed._
