By default, MFX handles PHP sessions automatically and uses cookies to do so.

Sessions management is handled by the Session Service.

The Session Service implements the `ISessionService` and `ArrayAccess` interfaces.

## Enforced Session Settings

In accordance with the [recommended secured session settings](https://www.php.net/manual/en/session.security.ini.php), MFX defines the following settings when the Session Service starts.

| Parameter                       | Value              |
| ------------------------------- | ------------------ |
| `session.use_cookies`           | `1`                |
| `session.use_only_cookies`      | `1`                |
| `session.use_strict_mode`       | `1`                |
| `session.cookie_httponly`       | `1`                |
| `session.use_trans_id`          | `0`                |
| `session.cookie_samesite`       | `Strict`           |
| `session.cache_limiter`         | `nocache`          |
| `session.sid_length`            | `48`               |
| `session.sid_bit_per_character` | `6`                |
| `session.hash_function`         | `sha256`           |
| `session.gc_maxlifetime`        | `900` (15 minutes) |
| `session.serialize_handler`     | `php_serialize`    |

## Session Customizable Settings

| Parameter               | Default Value                                           |
| ----------------------- | ------------------------------------------------------- |
| Session Name            | `MFXSESSION`                                            |
| Session Cookie Lifetime | `0` (the cookie will be removed when the browser quits) |
| Session Cookie Path     | `.`                                                     |
| Session Cookie Domain   | _Empty string_                                          |

### Customizing the Behavior of the Session Manager

You can customize any value above through the Session Manager's [configuration directives](Configuration-Directives#session-management).

You can also disable the Session Service completely by setting `session.enabled` to `false` in your configuration file. This allows you to handle sessions on your own terms, though most users won't need that.

Finally, you can disable the use of cookies by setting `session.use_cookies` to `false`. However, we strongly discourage disabling cookies as session ids will be sent in clear within the various URLs contained in your web pages. It is very likely that we will remove this option in the future.

## Storing Data In Sessions

As MFX closes sessions as soon as their data is read, direct changes to the `$_SESSION` global variable won't be saved.

Instead you have to rely on modification methods provided by the Session Service.

```php
// Setting multiple values at once
function setInSession(array $values): void;

// Unsetting multiple values at once
function unsetInSession(string ...$keys): void;

// Leveraging the ArrayAccess interface
// -- From inside a route
$sessionService = $this->serviceProdiver->getSessionService();
$sessionService['key'] = 'value';
unset($sessionService['key']);
```

> [!NOTE]
> As each call to modification methods opens and closes the session, it is highly recommended to use the methods allowing for multiple changes at once if you need to change several values to avoid unnecessary blocking IO.
