# CoreProfiler Class

[`chsxf\MFX`](API-Namespace-chsxf_MFX)

```php
final class CoreProfiler
```

## Summary

Core profiler class

Since `1.0`

## Methods

### getProfilingDuration

```php
public static function getProfilingDuration(): float|false
```

Evaluates how long was the profiling

Since `1.0`

#### Returns

`boolean|float` false if profiling is not initialized or complete, or the duration in milliseconds

---

### init

```php
public static function init()
```

Initiliases profiling

This function enables output buffering.

Since `1.0`

---

### pushEvent

```php
public static function pushEvent(string $event)
```

Push a custom event into profiling data

Since `1.0`

#### Parameters

| Name     | Type     | Description      |
| -------- | -------- | ---------------- |
| `$event` | `string` | Name of the even |

---

### stop

```php
public static function stop()
```

Terminates profiling and output buffering and echoes the result

Since `1.0`

---

