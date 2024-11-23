# ICoreServiceProvider Interface

[`chsxf\MFX\Services`](API-Namespace-Services)

```php
interface ICoreServiceProvider
```

## Summary

Core service provider interface

Since `2.0`

## Methods

### getAuthenticationService

```php
public abstract function getAuthenticationService(): IAuthenticationService
```

Gets the current authentication service

Since `2.0`

#### Returns

`IAuthenticationService` 

---

### getConfigService

```php
public abstract function getConfigService(): IConfigService
```

Gets the current configuration service

Since `2.0`

#### Returns

`IConfigService` 

---

### getDatabaseService

```php
public abstract function getDatabaseService(): IDatabaseService
```

Gets the current database service

Since `2.0`

#### Returns

`IDatabaseService` 

---

### getLocalizationService

```php
public abstract function getLocalizationService(): ILocalizationService
```

Gets the current localization service

Since `2.0`

#### Returns

`ILocalizationService` 

---

### getProfilingService

```php
public abstract function getProfilingService(): IProfilingService
```

Gets the current profiling service

Since `2.0`

#### Returns

`IProfilingService` 

---

### getRequestService

```php
public abstract function getRequestService(): IRequestService
```

Gets the current request service

Since `2.0`

#### Returns

`IRequestService` 

---

### getScriptService

```php
public abstract function getScriptService(): IScriptService
```

Gets the current script service

Since `2.0`

#### Returns

`IScriptService` 

---

### getSessionService

```php
public abstract function getSessionService(): ISessionService
```

Gets the current session service

Since `2.0`

#### Returns

`ISessionService` 

---

### getStyleSheetService

```php
public abstract function getStyleSheetService(): IStyleSheetService
```

Gets the current stylesheet service

Since `2.0`

#### Returns

`IStyleSheetService` 

---

### getTemplateService

```php
public abstract function getTemplateService(): ITemplateService
```

Gets the current template service

Since `2.0`

#### Returns

`ITemplateService` 

---

