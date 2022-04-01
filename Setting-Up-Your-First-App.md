## Folder Structure

At this point, your repository, if empty prior to the addition of the framework, should look like this:

```
📁 vendor
  📄 autoload.php
  📁 chsxf
  📁 composer
  ... and other things
```

## Adding the App Folder

Apps, constituting the "application layer" of any website based on MFX, are located in their own folder. Add a folder named `application` at the root level and a `config` folder in it.

You should end up with this folder structure:

```
📁 application
  📁 config
📁 vendor
  📄 autoload.php
  📁 chsxf
  📁 composer
  ... and other things
```

**Note:**\
The `application` folder can be renamed to suit your needs as you see fit.

## Adding Starter Files

You will need three files to be able to start working on your website:

* A configuration file
* A PHP entry point file
* A `.htaccess` file to setup URL rewriting with Apache

### Configuration File

Create a `config.php` file inside the `application/config` folder and paste these lines in it:

```php
<?php
use chsxf\MFX\Config;

Config::load([

]);
```

For now, we will keep the configuration file empty and add options in the following steps.

### Entry Point File

Usually, PHP entry point files are named `index.php`. In order to obfuscate things, the default entry point file is called `entrypoint.php` with MFX.

Create an `entrypoint.php` file at the root level of your website and paste these lines in it:

```php
<?php
use chsxf\MFX\Framework;

require_once('vendor/autoload.php');
Framework::init('application/config/config.php');
```

### Apache's `.htaccess` File

As stated earlier, MFX relies a lot on URL rewriting. So we have to setup Apache accordingly.

Create a `.htaccess` file at the root level of your website and paste these lines in it:

```
<IfModule mod_rewrite.c>
RewriteEngine On

RewriteBase /

RewriteCond %{REQUEST_FILENAME} !-f
RewriteCond %{REQUEST_FILENAME} !-d
RewriteRule ^(.+)_\d{10,}\.(js|xml|css|swf|png|jpg|gif)$ $1.$2 [L]

RewriteCond %{REQUEST_FILENAME} !-f
RewriteCond %{REQUEST_FILENAME} !-d
RewriteRule . /entrypoint.php [L]
</IfModule>

DirectoryIndex entrypoint.php
```

> **IMPORTANT NOTE:**\  
> The `.htaccess` file above is designed for setups with virtual hosts targetting the root folder directly. If your local development setup in placed in a sub-folder of your webserver (for example, `http://localhost/my-website-subfolder/`), you have to adapt the file as follow:
> 
> * Replace `RewriteBase /`  with `RewriteBase /path/to/your/website/subfolder`
> * Replace `RewriteRule . /entrypoint.php [L]` with `RewriteRule . /path/to/your/website/subfolder/entrypoint.php [L]`

## Resulting Folder Structure

At this point, your repository should look like this:

```
📄 .htaccess
📁 application
  📁 config
    📄 config.php
📄 entrypoint.php
📁 vendor
  📄 autoload.php
  📁 chsxf
  📁 composer
  ... and other things
```

Now try to access your website, you should get this result:

```
200 OK
```

If not, you've missed something.

## Next Step

[[Building Your First Route]]
