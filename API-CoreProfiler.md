# CoreProfiler Class

[`chsxf\MFX`](API-Namespace-chsxf_MFX)

```php
final class CoreProfiler implements Services\IProfilingService
```

## Summary

Core profiler class

Since `1.0`

## Methods

### __construct

```php
public function __construct(bool $active)
```

Constructor

Since `2.0`

---

### getProfilingDuration

```php
public function getProfilingDuration(): float|false
```

Evaluates how long was the profiling

Since `2.0`

#### Returns

`boolean|float` false if profiling is not initialized or complete, or the duration in milliseconds

---

### isActive

```php
public function isActive(): bool
```

Tells if the profiler is active or not

Since `2.0`

#### Returns

`bool` 

---

### pushEvent

```php
public function pushEvent(string $event): void
```

Push a custom event into profiling data

Since `2.0`

#### Parameters

| Name     | Type     | Description      |
| -------- | -------- | ---------------- |
| `$event` | `string` | Name of the even |

---

