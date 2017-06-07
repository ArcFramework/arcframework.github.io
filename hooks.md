# Hooks

One of the strengths of Wordpress is it's comprehensive system of hooks which can be used to trigger code
during different stages of the execution of Wordpress core. While powerful and extensible, the hooks
system can also be confusing which is why we've included a few wrappers around Wordpress's own API to make
the process of registering hooks a little more intuitive. Of course, if you prefer the wordpress API you
are free to use that directly instead.

## Plugin Activation

To define what should be done when your plugin is activated, you can use the `Arc\Hooks\Activation` object
like this:

```php

namespace Vendor\Plugin;

use Arc\Hooks\Activation;

class Plugin extends BasePlugin
{
    public function run(Activation $activation)
    {
        $activation->whenPluginIsActivated(function() {
            // Do something
        });

        $activation->whenPluginIsDeactivated(function() {
            // Do something else
        });
    }
}
```

In the above example we are taking advantage of dependency injection provided by the Illuminate IoC
container to automatically inject the Activation class into the run() method of the plugin.

## Admin Menus 

### Create an admin page under 'Settings' in the wp-admin sidebar

A good place to register admin menus would be in a service provider. Here are the minimum
settings you need to pass in to register an admin menu for your plugin.

    <?php

    namespace MyVendor\MyPlugin\Providers;

    use Arc\Admin\AdminMenus;
    use Illuminate\Support\ServiceProvider;

    class AdminMenusServiceProvider extends ServiceProvider
    {
        /**
         * Bootstrap the application services.
         *
         * @return void
         */
        public function boot(AdminMenus $adminMenus)
        {
            // Create the settings page
            $adminMenus-&gt;addSettingsPage()
                -&gt;whichRendersView('admin.settings')
                -&gt;withSettings([
                    'my_plugin_some_setting'
                ])-&gt;add();
        }
    }
