# IProfilingService Interface

[`chsxf\MFX\Services`](API-Namespace-Services)

```php
interface IProfilingService
```

## Summary

Profiling service interface

Since `2.0`

## Methods

### getProfilingDuration

```php
public abstract function getProfilingDuration(): float|false
```

Gets the total profiling duration, or false if the profiler is either not active or profiling is not done

Since `2.0`

#### Returns

`float|false` 

---

### isActive

```php
public abstract function isActive(): bool
```

Tells if the the profiling service is enabled or not

Since `2.0`

#### Returns

`bool` 

---

### pushEvent

```php
public abstract function pushEvent(string $event): void
```

Pushes an event into the profiling data

Since `2.0`

#### Parameters

| Name     | Type     | Description        |
| -------- | -------- | ------------------ |
| `$event` | `string` | Event name to push |

---

