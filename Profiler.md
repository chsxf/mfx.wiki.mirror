[Profiling](<https://en.wikipedia.org/wiki/Profiling_(computer_programming)>) your PHP application is important to ensure your code is as efficient as possible. One of the most known profiler for PHP is [Xdebug](https://xdebug.org/).

However, setting up a profiler can be tedious, or even impossible, especially on shared hosting. That's why MFX provides a built-in profiler.

## Limitations

MFX's profiler is not meant to replace low-level tools like Xdebug.

Most importantly, the profiler runs at the application level, among the rest of your PHP code, and therefore can impact performance and memory consumption readings significantly.

However, it remains useful as a comparison tool when optimizing your code.

## Enabling the Profiler

You have two ways to implement the profiler:

- through the configuration file if you want to run the profiler on every request (through the `profiling` [configuration directive](Configuration-Directives#profiler))
- manually if you want to run it selectively on certain routes or sections of the code

**Important note:** Either way, it is strongly discouraged to run the profiler in production environments.

To start and stop a manual profiling session, you have to call the `init()` and `stop()` functions from the [CoreProfiler](API-CoreProfiler) class.

A session do not need to start at the top of a request and stop at the end. You can start and stop the profiler at any time. However, once a session is complete, you can't restart it until the next request.

## Pushing Events

Interpreting profiling results can be complex. That's why the profiler offers the option to push events to the profiling timeline. Use the `CoreProfiler::pushEvent(string $event)` function to push an event.

We recommend pushing "opening" and "closing" events for delimiting some sections of your code, like `"Database Query Start"` and `"Database Query End"` for example.

## Results

When the profiler is enabled, results will be flushed at the end of the response, either in a graphical way when the server outputs HTML, or in a synthetic way in plain text responses.
