Even if MFX will most likely be run most of the time through a web server, MFX applications can be run from the command-line too.

## Usage

Use the following command to execute your MFX application from the command-line:

```
php path/to/mfx/entrypoint.php [-- [options] [route]]
```

**\*Important Note**: For now, you have to execute your MFX application from your application's root folder.\*

### Arguments

| Argument                     | Description                                                                                                                                                                                                                  |
| ---------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `path/to/mfx/entrypoint.php` | Refers to the path to your entry point file (as explained in the [Setting Up Your First App](Setting-Up-Your-First-App#entry-point-file)). If you followed the default guidelines, the path should just be `entrypoint.php`. |
| `route`                      | The route you want to call. If this parameter is omitted, the default route is called.                                                                                                                                       |

### Options

| Option                        | Description                                                                                         |
| ----------------------------- | --------------------------------------------------------------------------------------------------- |
| `--config path/to/config.php` | If this option is specified, you can override the default configuration file used for this instance |
