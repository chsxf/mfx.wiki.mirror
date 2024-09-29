MFX services can be accessed through the Core Service Provider, which implements the `ICoreServiceProvider` interface.

## Access From a Route

When a route provider extends from `BaseRouteProvider`, you can access the Core Service Provider from any route implement as an instance method.

```php
#[Route, AnonmousRoute]
public function myRoute(array $params): void {
    $sp = $this->serviceProvider;
    // ...
}
```

## Service Getters

Once you have access to the Core Service Provider, you can obtain a reference to any services through the following methods:

```php
function getAuthenticationService(): IAuthenticationService;
function getConfigService(): IConfigService;
function getDatabaseService(): IDatabaseService;
function getLocalizationService(): ILocalizationService;
function getProfilingService(): IProfilingService;
function getRequestService(): IRequestService;
function getScriptService(): IScriptService;
function getSessionService(): ISessionService;
function getStyleSheetService(): IStyleSheetService;
function getTemplateService(): ITemplateService;
```

### Example

```php
#[Route, AnonmousRoute]
public function myRoute(array $params): void {
    $authService = $this->serviceProvider->getAuthenticationService();
    // ...
}
```
