# Shortcodes

One of the most common operations for plugin developers is defining shortcodes. Arc has a fluent way to do this to make the code a little more expressive:

## Defining Shortcodes

To define a shortcode we use the `Arc\Shortcode\Shortcodes` object like this:

```php

namespace Vendor\Plugin\Providers;

use Arc\Shortcode\Shortcodes;
use Illuminate\Support\ServiceProvider;

class ShortcodeProvider extends ServiceProvider
{
    public function boot(Activation $activation)
    {
        // Register the plugin's shortcodes
        $this->app
            ->make(Shortcodes::class)
            ->code('my-shortcode')
            ->rendersView('shortcodes.my-shortcode')
            ->code('my-other-shortcode')
            ->rendersView('shortcodes.my-other-shortcode')
            ->register();
    }
}
```

In the above example we are performing the task of dependency injection by using the make method provided by the Illuminate IoC container (`$this->app`) to automatically instantiate the Shortcodes class without worrying about it's dependencies.

## Shortcode Views 

When you define a shortcode with the `rendersView()` fluent method, you can pass the name of a blade view into the method to define what html is output when the shortcode is used on the website.  
