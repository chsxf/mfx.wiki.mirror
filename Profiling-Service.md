[Profiling](<https://en.wikipedia.org/wiki/Profiling_(computer_programming)>) your PHP application is important to ensure your code is as efficient as possible. One of the most known profiler for PHP is [Xdebug](https://xdebug.org/).

However, setting up a profiler can be tedious, or even impossible, especially on shared hosting. That's why MFX provides a built-in Profiling Service.

## Limitations

MFX's Profiling Service is not meant to replace low-level tools like Xdebug.

Most importantly, the Profiling Service runs at the application level, among the rest of your PHP code, and therefore can impact performance and memory consumption readings significantly.

However, it remains useful as a comparison tool when optimizing your code.

## Enabling the Profiling Service

You enable the Profiling Service in the configuration file (through the `profiling` [configuration directive](Configuration-Directives#profiler))

It will run on every request.

> [!CAUTION]
> It is strongly discouraged to run the Profiling Service in production environments.

## Pushing Events

Interpreting profiling results can be complex. That's why the Profiling Service offers the option to push events to the profiling timeline. Use the following function to push an event:

```php
function pushEvent(string $event): void;
```

We recommend pushing "opening" and "closing" events for delimiting some sections of your code, like `"Database Query Start"` and `"Database Query End"` for example.

## Results

When the Profiling Service is enabled, results will be flushed at the end of the response, either in a graphical way when the server outputs HTML, or in a synthetic way in plain text responses.
