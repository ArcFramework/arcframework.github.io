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

When you define a shortcode with the `rendersView()` fluent method, you can pass the name of a blade view into the method to define what html is output when the shortcode is used on the website. For example, if you have a view located in a file called `/resources/views/task/create.blade.php` you could make the shortcode render that view like so:

    $shortcodes->code('create-task')
        ->renderView('task.create');

If you would like to pass a variable for use in that view, you can do so in the second parameter of `renderView()`.

    $shortcodes->code('create-task')
        ->renderView('task.create', [
            'projects' => $myProjects
        ]);

The above would make a variable valled `$projects` available in the view which would be set to the value of `$myProjects`.

## Shortcode Attributes

When you define a shortcode which renders a view, that view will have available it three variables automatically as well as any additional parameters which you passed in via the second argument of `renderView()`:

### `$attributes`, `$content` and `$shortcodeName`

For example, suppose we define a shortcode called `my-shortcode` which renders a view located in `/resources/views/shortcodes/my-shortcode.blade.php`. and pass in an attribute called `foo` like so:

    $shortcodes->code('my-shortcode')->renderView('shortcodes.my-shortcode');

And then on the page pass in an attribute called `foo` with a value of `"bar"`:

    [my-shortcode foo="bar"] Some content here [/my-shortcode]
    
Then in the view template `/resources/views/shortcodes/my-shortcode.blade.php` we will have access to the following variables:

    $shortcodeName = 'my-shortcode';
    $content = ' Some content here ';
    $attributes = ['foo' => 'bar'];
