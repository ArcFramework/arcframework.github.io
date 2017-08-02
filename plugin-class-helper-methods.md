# Plugin Class Helper Methods

Because an Arc plugin exists in the multi-tenanted environment of WordPress plugins we must avoid most of Laravel's global helpers to avoid collisions. For this reason the `Plugin` class of your plugin includes many nifty helper methods which are based on Laravel's own global helpers.

## `baseUrl()`

Returns the base URL of the Wordpress instance which is running the Arc plugin. For example:

    // Returns "http://mywebsite.com"
    \MyCompany\MyPluginName\Plugin::plugin()->baseUrl();
    
## `resourcePath()`

Returns the file path of the plugin's resources directory. For example:

    // Returns "/var/www/localhost/wp-content/plugins/my-plugin-name/resources"
    \MyCompany\MyPluginName\Plugin::plugin()->resourcePath();
