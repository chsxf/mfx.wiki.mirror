Protocols are an important part of a URL. `http` and `https`, among many others, are at the forefront of each one.

However, when working within the confine of a framework, it can be tedious to remember the path of specific resources, like images, scripts or style sheets. That's why MFX introduces **Fake Protocols**.

## Description of a Fake Protocol

Fake protocols have the same structure as regular protocols, but they can be translated to actual protocols to easily address specific resources.

For example, MFX defines a `mfxjs` fake protocol that, by default, targets `vendor/chsxf/mfx/static/js/`. So, when using the URL `mfxjs://somescript.js`, MFX will translate it to `vendor/chsxf/mfx/static/js/somescripts.js` automatically.

## Setting Up Fake Protocols

Fake protocols are defined once at startup through the `fake_protocols` [configuration directive](Configuration-Directives#fake-protocols).

### Example

```php
'fake_protocols' => [
    'js' => 'application/static/js',
    'css' => 'application/static/css'
]
```

## Manual Translation of a Fake Protocol

Fake protocol are automatically translated when the pages are sent to the browser. However, you may want to translate some URLs manually on occasion.

To that purpose, use the `CoreManager::convertFakeProtocols(string $str)` method.

### Example

```php
$str = 'My translated URL is mfxjs://test.js';
echo CoreManager::convertFakeProtocols($str);
// Will output:
// My translated URL is vendor/chsxf/mfx/static/js/test.js
```

## Default Fake Protocols

MFX defines several fake protocols by default, allowing easy access to static files provided by the framework:

| Key      | Default Path                  |
| -------- | ----------------------------- |
| `mfxjs`  | `vendor/chsxf/mfx/static/js`  |
| `mfxcss` | `vendor/chsxf/mfx/static/css` |
| `mfximg` | `vendor/chsxf/mfx/static/img` |
