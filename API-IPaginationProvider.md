# IPaginationProvider Interface

[`chsxf\MFX`](API-Namespace-chsxf_MFX)

```php
interface IPaginationProvider
```

## Summary

Interface describing objects that provide pagination information

Since `1.0`

## Methods

### defaultPageCount

```php
public abstract function defaultPageCount(): int
```

Retrieves the default number of items to display per page

Since `1.0`

#### Returns

`int` 

---

### totalItemCount

```php
public abstract function totalItemCount(): int
```

Retrieves the total number of items

Since `1.0`

#### Returns

`int` 

---

