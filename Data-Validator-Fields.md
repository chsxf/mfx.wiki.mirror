Fields describe the various items contained in your data structure.

At least, they are defined thanks to a name and a type, but you can also control the following aspects:

- they can be enabled or not,
- they can be set as read-only,
- they can have a default value,
- they can be generated with or without their current value,
- they can be repeatable and contain indexed array values,
- and finally, you can add [filters](Data-Validator-Filters) to alter how they are validated

Look at the [documentation of the Field class](API-DataValidator-Field) for more information.

## Field Types

Most built-in HTML types like `CHECKBOX`, `DATE`, `EMAIL`, or `TEXT` are included. But the data validator also provides custom field types like `POSITIVE_INTEGER` (a strictly positive integer number), `NEGATIVEZERO_INTEGER` (a negative or zero integer number), or `MULTI_SELECT` (same as `SELECT` but with enabled multiple selection).

| Field Type             | HTML Type  | HTML Extras Attributes |
| ---------------------- | ---------- | ---------------------- |
| `CHECKBOX`             | `checkbox` |                        |
| `COLOR`                | `color`    |                        |
| `DATE`                 | `date`     |                        |
| `EMAIL`                | `email`    |                        |
| `FILE`                 | `file`     |                        |
| `HIDDEN`               | `hidden`   |                        |
| `INTEGER`              | `number`   |                        |
| `LOWERCASE_WORD`       | `text`     |                        |
| `MONTH`                | `month`    |                        |
| `MULTI_SELECT`         | `select`   | `multiple`             |
| `NEGATIVE_INTEGER`     | `number`   | `max="-1"`             |
| `NEGATIVEZERO_INTEGER` | `number`   | `max="0"`              |
| `NUMBER`               | `number`   |                        |
| `PASSWORD`             | `password` |                        |
| `POSITIVE_INTEGER`     | `number`   | `min="1"`              |
| `POSITIVEZERO_INTEGER` | `number`   | `min="0"`              |
| `RADIO`                | `radio`    |                        |
| `RANGE`                | `range`    |                        |
| `SELECT`               | `select`   |                        |
| `TEL`                  | `tel`      |                        |
| `TEXT`                 | `text`     |                        |
| `TEXTAREA`             | `textarea` |                        |
| `TIME`                 | `time`     |                        |
| `UPPERCASE_WORD`       | `text`     |                        |
| `URL`                  | `url`      |                        |
| `WEEK`                 | `week`     |                        |
| `WORD`                 | `text`     |                        |

## Fields With Options

Three field types behave differently from the others: `SELECT`, `MULTI_SELECT`, and `RADIO`, as they require options to display multiple potential items eligible for validation.

Instance of these field types present two specific functions: `addOption` and `addOptions` to fill in the various options to display and validate against.

Look at the [documentation of the WithOptions class](API-DataValidator_Fields-WithOptions) for more information.

## Repeatable Fields

You can declare a field as repeatable. It means the field can contain more than one value. Multiple values are then accessed through their zero-based index, just as with a regular array.

Repeatable fields will be represented with the name array syntax. A field named `test` will then be exported to HTML as `test[]` by the data validator.

When enabling repetition for a field, you can assign a maximum number of occurences if needed.
