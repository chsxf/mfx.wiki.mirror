# PaginationManager Class

[`chsxf\MFX`](API-Namespace-chsxf_MFX)

```php
final class PaginationManager
```

## Summary

Helper class for managing pagination

Since `1.0`

## Methods

### __construct

```php
public function __construct(IPaginationProvider $provider, array $extraParameterKeys = array())
```

Constructor

Since `1.0`

#### Parameters

| Name           | Type                  | Description                               |
| -------------- | --------------------- | ----------------------------------------- |
| `$provider`    | `IPaginationProvider` | Pagination information provider           |
| `$extraParams` | `array`               | Extra parameter keys for further requests |

---

### addCurrentPageDataValidatorFields

```php
public function addCurrentPageDataValidatorFields(DataValidator $validator)
```

Adds current page parameters to the specified DataValidator instance

Since `1.0`

#### Parameters

| Name         | Type            | Description |
| ------------ | --------------- | ----------- |
| `$validator` | `DataValidator` |             |

---

### getCurrentPageIndex

```php
public function getCurrentPageIndex(): int
```

Computes the 0-based current page index

Since `1.0`

#### Returns

`int` 

---

### getCurrentPageStart

```php
public function getCurrentPageStart(): int
```

Tells the start index for the current page

Since `1.0`

#### Returns

`int` 

---

### getCurrentPageURLParams

```php
public function getCurrentPageURLParams(bool $includeExtraParameters = true): string
```

Gets the URL parameters for the current page

Since `1.0`

#### Parameters

| Name                      | Type      | Description                                             |
| ------------------------- | --------- | ------------------------------------------------------- |
| `$includeExtraParameters` | `boolean` | If set, includes the extra parameters in the URL params |

#### Returns

`string` 

---

### getItemCountPerPage

```php
public function getItemCountPerPage(): int
```

Tells how many items should be displayed per page

Since `1.0`

#### Returns

`int` 

---

### getPagesCount

```php
public function getPagesCount(): int
```

Tells how many pages exists

Since `1.0`

#### Returns

`int` 

---

### getTotalItemCount

```php
public function getTotalItemCount(): int
```

Tells the total count of items

Since `1.0`

#### Returns

`int` 

---

### hasNextPage

```php
public function hasNextPage(): bool
```

Tells if a next page exists

Since `1.0`

#### Returns

`boolean` 

---

### hasPrevPage

```php
public function hasPrevPage(): bool
```

Tells if a previous page exists

Since `1.0`

#### Returns

`boolean` 

---

### nextPageStart

```php
public function nextPageStart(): int
```

Gets the next page start index

Since `1.0`

#### Returns

`int` 

---

### nextPageURLParams

```php
public function nextPageURLParams(bool $includeExtraParameters = true): string
```

Gets the next page URL parameters

Since `1.0`

#### Parameters

| Name                      | Type      | Description                                             |
| ------------------------- | --------- | ------------------------------------------------------- |
| `$includeExtraParameters` | `boolean` | If set, includes the extra parameters in the URL params |

#### Returns

`string` 

---

### pageStart

```php
public function pageStart(int $pageIndex): int
```

Gets the start index of the specified page

Since `1.0`

#### Parameters

| Name         | Type  | Description |
| ------------ | ----- | ----------- |
| `$pageIndex` | `int` | Page index  |

#### Returns

`int` 

---

### pageURLParams

```php
public function pageURLParams(int $pageIndex, bool $includeExtraParameters = true): string
```

Get the URL parameters of the specified page

Since `1.0`

#### Parameters

| Name                      | Type   | Description                                             |
| ------------------------- | ------ | ------------------------------------------------------- |
| `$pageIndex`              | `int`  | Page index                                              |
| `$includeExtraParameters` | `bool` | If set, includes the extra parameters in the URL params |

#### Returns

`string` 

---

### prevPageStart

```php
public function prevPageStart(): int
```

Gets the previous page start index

Since `1.0`

#### Returns

`int` 

---

### prevPageURLParams

```php
public function prevPageURLParams(bool $includeExtraParameters = true): string
```

Gets the previous page URL parameters

Since `1.0`

#### Parameters

| Name                      | Type      | Description                                             |
| ------------------------- | --------- | ------------------------------------------------------- |
| `$includeExtraParameters` | `boolean` | If set, includes the extra parameters in the URL params |

#### Returns

`string` 

---

### setExtraParameter

```php
public function setExtraParameter(string $key, mixed $value)
```

Sets a registered extra parameter's value

Since `1.0`

#### Parameters

| Name     | Type     | Description           |
| -------- | -------- | --------------------- |
| `$key`   | `string` | Extra parameter's key |
| `$value` | `mixed`  | A scalar value        |

---

### sqlLimit

```php
public function sqlLimit(): string
```

Generates a SQL LIMIT clause based on current page information

Since `1.0`

#### Returns

`string` 

---

