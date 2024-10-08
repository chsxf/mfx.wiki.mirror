# DoNotExistInDB Class

[`chsxf\MFX\DataValidator\Filters`](API-Namespace-DataValidator_Filters)

```php
class DoNotExistInDB extends ExistsInDB
```

## Summary

Description of a filter validating if the specified value exists in a database table

Since `1.0`

## Methods

### __construct

```php
public function __construct(string $table, string $field, ?string $message, DatabaseConnectionInstance $connection)
```

Constructor

Since `1.0`

#### Parameters

| Name          | Type                         | Description                      |
| ------------- | ---------------------------- | -------------------------------- |
| `$table`      | `string`                     | Database table name              |
| `$field`      | `string`                     | Database field name              |
| `$message`    | `string`                     | Error message (Defaults to NULL) |
| `$connection` | `DatabaseConnectionInstance` | Database connection instance     |

---

