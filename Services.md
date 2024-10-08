Most features of MFX are available to routes through services:

- [[Authentication Service]]
- [[Configuration Service]]
- [[Database Service]]
- [[Localization Service]]
- [[Profiling Service]]
- [[Request Service]]
- [[Script Service]]
- [[Session Service]]
- [[Stylesheet Service]]
- [[Template Service]]

## Accessing Services

For your route to gain access to services, its provider must derive from the `BaseRouteProvider` class (and not implement the `IRouteProvider` interface only).

In complement, the route must also be an instance method.

Then, inside your route you can access the [[Core Service Provider]] to reach any available services you may need.

### Example

```php
use chsxf\MFX\Attributes\Route;
use chsxf\MFX\Routers\BaseRouteProvider;

class TestRouteProvider extends BaseRouteProvider
{
    #[Route]
    public function testRoute(array $params) {
        // Use this command to access the config service
        $configService = $this->serviceProvider->getConfigService();
        // ...
    }
}
```
