## Folder Structure

At this point, your repository, if empty prior to the addition of the framework, should look like this:

```
📁 .git
📄 .gitmodules
📁 mfx
```

## Adding the App Folder

Apps, constituting the "application layer" of any website based of mfx, are located in their own folder. Add a folder named `app` at the root level and a `config` folder in it.

You should end up with this folder structure:

```
📁 .git
📄 .gitmodules
📁 app
  📁 config
📁 mfx
```

**Note:**\
The `app` name for the folder can be changed to fit your needs.

## Adding Starter Files

You will need three files to be able to start working on your website:

* A configuration file
* A PHP entry point file
* A `.htaccess` file to setup URL rewriting with Apache


### Configuration File

Create a `config.php` file inside the `app/config` folder and paste these lines in it:

```php
<?php
\CheeseBurgames\MFX\Config::load(array(

));
```

### Entry Point File

Usually, PHP entry point file are named `index.php`. In order to obfuscate things and make it more difficult to hackers to break the framework, the default entry point file is called `entrypoint.php` with <abbr title="php-micro-framework in short">MFX</abbr>.

Create an `entrypoint.php` file at the root level of your website and paste these lines in it:

```php
<?php
chdir(dirname(__FILE__));
define('MFX_CONFIG_FILE_PATH', 'app/config/config.php');
require_once('mfx/framework/framework.php');
```

### Apache's `.htaccess` File

As stated earlier, <abbr title="php-micro-framework in short">MFX</abbr> relies a lot on URL rewriting. So we have to setup Apache accordingly.

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
> The `.htaccess` file above is designed for setups with virtual hosts targetting the root folder directly. If your local development setup in placed in a sub-folder of your webserver (ie `http://localhost/my-website-subfolder/`), you have to adapt the file as follow:
> 
> * Replace `RewriteBase /`  with `RewriteBase /path/to/your/website/subfolder`
> * Replace `RewriteRule . /entrypoint.php [L]` with `RewriteRule . /path/to/your/website/subfolder/entrypoint.php [L]`

## Resulting Folder Structure

At this point, your repository should look like this:

```
📁 .git
📄 .gitmodules
📄 .htaccess
📁 app
  📁 config
    📄 config.php
📄 entrypoint.php
📁 mfx
```

However, we're not ready yet. If you try to access your website, you will get this error:

```
400 Bad Request
Uncaught ErrorException: '' is not a valid route.
#0 /path/to/website/mfx/framework/framework.php(87): CheeseBurgames\MFX\CoreManager::handleRequest(Object(Twig_Environment), NULL)
#1 /path/to/website/entrypoint.php(4): require_once('/path/to/webs...')
#2 {main}
```

If you get it, you're good! If not, you've missed something.

## Next Step

[[Building Your First Route]]
