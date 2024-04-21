# IMessageDispatcher Interface

[`chsxf\MFX\DataValidator`](API-Namespace-DataValidator)

```php
interface IMessageDispatcher
```

## Summary

Interface describing data validator's message dispatchers

Since `1.0`

## Methods

### dispatchMessage

```php
public abstract function dispatchMessage(string $message, int $level)
```

Dispatches a message

Since `1.0`

#### Parameters

| Name       | Type     | Description                            |
| ---------- | -------- | -------------------------------------- |
| `$message` | `string` | Message to dispatch                    |
| `$level`   | `int`    | Error level of the message to dispatch |

---

