# Hooks

One of the strengths of Wordpress is it's comprehensive system of hooks which can be used to trigger code
during different stages of the execution of Wordpress core. While powerful and extensible, the hooks
system can also be confusing which is why we've included a few wrappers around Wordpress's own API to make
the process of registering hooks a little more intuitive. Of course, if you prefer the wordpress API you
are free to use that directly instead.

## Plugin Activation

To define what should be done when your plugin is activated, you can use the `Arc\Hooks\Activation` object
like this:

```php7
<?php

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
