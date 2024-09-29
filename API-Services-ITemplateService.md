# ITemplateService Interface

[`chsxf\MFX\Services`](API-Namespace-Services)

```php
interface ITemplateService
```

## Summary

Template service interface

Since `2.0`

## Methods

### convertFakeProtocols

```php
public abstract function convertFakeProtocols(string $str): string
```

Converts fake protocols in the provided string

Since `2.0`

#### Parameters

| Name   | Type     | Description  |
| ------ | -------- | ------------ |
| `$str` | `string` | Input string |

#### Returns

`string` The converted string with expanded fake protocols

---

### getTwig

```php
public abstract function getTwig(): ?Twig\Environment
```

Retrieves the current Twig environment if existing

Since `2.0`

#### Returns

`null|Environment` 

---

