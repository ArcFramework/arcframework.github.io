## Where do I put my code?

Good question. There are a few different approaches you could try:

### Plugin::run() method

Add a `run()` method to your `Plugin` class which is created in the root `app/` directory when you install the plugin
boilerplate. If it exists, this method will be automatically called when the plugin is booted, and any typehinted parameters
will be automatically injected via the service container.

### Service Providers

You could create service providers which you could use to bind your dependencies and bootstrap components of your plugin.

## Shipping The Plugin

To a produce a shippable zip file of your plugin when it's ready you can use the `php arc ship` command in Arc's 
`artisan`-esque `arc` CLI tool. This will "compile" a zip file of your plugin without dev dependencies and with all files and
directories named in the `.shipignore` file deleted. The file will be named automatically according to the version number you
have named in your main plugin file, so make sure you bump the version number each time you run the command. By default these
files are saved in your home directory with the plugin name as a subdirectory formatte like this: 
`~/plugin-name/plugin-name-1.0.0.zip`. If you wish to customise where the Arc plugins are shipped to you can set a default
with an `~/.arc/config.php` file.

    /*
     |---------------------------
     | Arc Framework CLI Config
     |---------------------------
     */

    return [
        'shippedPluginDirectory' => '/Users/Me/plugins`
    ];
