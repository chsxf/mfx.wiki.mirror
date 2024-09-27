The Database Service provides a simple way to handle database connections, opening and closing them as requested.

The Database Service implements the `IDatabaseService` interface.

## Accessing The Database Service

You can access the Database Service through the core service provider in your routes:

```php
$databaseService = $this->serviceProvider->getDatabaseService();
```

## Opening a Connection

Use this method to open a connection:

```php
function open(string $server = '__default', bool $forceNew = false): DatabaseConnectionInstance;
```

By default, without any parameter, the Database Service will try to open a connection to the database server referenced as `__default` in the configuration, or reuse a previously opened connection if such exists. For this call to work, a `__default` connection must exist in your configuration file.

Even if most users will only need to open connections to a single database server, MFX allows for several in the [configuration directives](Configuration-Directives#database-management). You can provide any other existing connection name for the `$server` parameter to open or reuse an existing connection object to another database.

If `$forceNew` is set to `true`, the Database Service will try to open a new connection to the database even if another opened connection already exists.

The function returns the requested connection instance, or throws a `chsxf\PDO\DatabaseManagerException` if an error occurs.

The `DatabaseConnectionInstance` class inherits from the `DatabaseManager` class from the [`pdo-database-manager`](https://github.com/chsxf/pdo-database-manager) package, and comes with all the same benefits (helpers improving query management, error logging, ...). Please refer to the [corresponding documenation](https://github.com/chsxf/pdo-database-manager) for more information.

## Closing a Connection

As any other PHP processes that do not use persistant connections to database servers, MFX will close all database connections at the end of each request.

Howerver by using the connection instances returned by `open`, you can explictly close a connection at any moment. Database instances being heavily used for most requests of a website or API, it is important to preserve them as much as possible. So you may want to cut connections as soon as possible, especially if you have long processes after your database queries have finished.

To close a connection, just call the following method:

```php
function close(DatabaseConnectionInstance &$connectionInstance);
```

_Note: Unsetting the connection instance is not enough to close a connection as the Database Service keeps track of all opened connection to be able to reuse them if needed._
