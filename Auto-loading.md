Auto-loading is handled through Composer's [`autoload` directive](https://getcomposer.org/doc/04-schema.md#autoload).

If you followed our [[Getting Started]] procedure, you already used it when [[Building Your First Route]].

You can add any path you like to your `composer.json` file to auto-load your custom routes and types.

Here is an example:

```json
"autoload": {
  "psr-4": {
    "": [ "application/routes", "application/classes", "application/interfaces" ],
    "MyNamespace\\": "path/to/classes/for/this/namespace"
  }
}
```

**Important Note:** Don't forget to run `composer update` afterwards.
