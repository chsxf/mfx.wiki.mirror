Filters are an essential part of the data validation process, as they allow you to alter how fields and their values are validated.

Filters can be easily added to a field thanks to the `addFilter` method. It is also very easy to create custom fields to extend the capabilities of the data validator to meet your needs.

## Built-in Filters

| Filter               | Description                                                                                                                | Apply On |
| -------------------- | -------------------------------------------------------------------------------------------------------------------------- | -------- |
| `DoNotExistInDB`     | Checks if a field's value does not exist in a table's column of the database                                               | Values   |
| `ExistsInDB`         | Checks if a field's value exists in a table's column of the database                                                       | Values   |
| `In`                 | Checks if a field's value exists in a list of options                                                                      | Values   |
| `InFloatRange`       | Checks if a field's value is comprised between two floating point values                                                   | Values   |
| `InIntRange`         | Checks if a field's value is comprised between two integer values                                                          | Values   |
| `IsOfType`           | Checks if a field's value is of a specific type (boolean, string, int, etc)                                                | Values   |
| `LogicOr`            | This filter is a container for other filters. It will be considered valid if any of the contained filters is deemed valid. | Values   |
| `MatchFilter`        | Checks if a field's value matches those of one or more other fields                                                        | Values   |
| `Path`               | Checks if a field's value is matching the path of an existing file                                                         | Values   |
| `RegExp`             |  Checks if a field's value is matching a regular expression                                                                | Values   |
| `RequiredIfNotEmpty` | Checks that a field contains a value if another field is not empty                                                         | Values   |
| `Unique`             | Checks that a field, most likely repeatable, contains only unique values                                                   | Fields   |

## Writing a Custom Filter

Let's say you want to write a filter to check if a field's value is even.

Here's how you would do that:

```php
use chsxf\MFX\DataValidator\AbstractFilter;

class IsEven extends AbstractFilter {

    public function __construct(string $message = NULL) {
        if ($message === NULL) {
            $message = "The value of the '%s' field must be even";
        }
        parent::__construct($message);
    }

    public function validate(string $fieldName, mixed $value, int $atIndex = -1, bool $silent = false): bool {
        if (!is_numeric($value) || intvalue($value) % 2 != 0) {
            $this->emitMessage($fieldName);
            return false;
        }
        return true;
    }

}
```
