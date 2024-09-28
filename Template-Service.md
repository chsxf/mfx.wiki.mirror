MFX uses [Twig](https://twig.symfony.com/) as its template engine.

The Template Service gives you access the Twig environment, among other features. It implements the `ITemplateService` interface.

## Getting a Reference to the Twig Environment

Use this method to get access to the Twig environment:

```php
function getTwig(): ?Environment;
```

## Other Features

The Template Service also allows you to convert [[Fake Protocols]].
