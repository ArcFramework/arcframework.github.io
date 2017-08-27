# Custom Post Types

One of the most common things you will do as a Wordpress plugin developer is to set up custom post types for your plugin. Arc provides a simple way to do this out of the box without referencing all the various dynamically named hooks that are neccessary to customize the way your custom post type appears and behaves. In Arc, a custom post type is automatically set up as an Eloquent model which extends the built in `Arc\Models\Post` model allowing you to use the power of eloquent for querying and updating your custom post type data.

## Creating a custom post type

To create a custom post type, use the arc cli generator command:

`php arc make:type "My Custom Post Type"`

This will generate a file in your `app/CustomPostTypes` directory called `MyCustomPostType.php`. The class contained in this file contains all the boilerplate you need to quickly and easily set up your custom post type.

## Configuring a custom post type

### Slug

The generator command will create a default slug based on the name of the post type. You can change this to whatever you like by editing the `$slug` property in the class. Remember that changing this slug is neccessary for querying the database, so when changing the slug after having created posts of this type you will also need to change the value of the `post-type` column of those posts in the database.

    protected $slug = 'my-custom-post-type-name';

### Name

    protected $name = 'My Custom Post Type';

### Plural Name

    protected $pluralName = 'My Custom Post Types';

### Public

    protected $public = true;
    
This boolean determines whether or not the individual posts of this type can be viewed by non authenticated users.

### Icon

    protected $icon = 'dashicons-admin-home';

Add the slug of the desired icon for the admin menu.

### View

    protected $view = 'custom-post-types.my-custom-post-type.show';

If you would like to use a blade view for displaying the post, you can include the key of that view in the `$view` property.

### Show in different admin menu

If you would like to nest the admin page for your custom post type under another menu item, add the set the `$showInMenu` property to the key of that meny item.

    protected $showInMenu = 'my-plugin';

### Customise headers of the admin columns

To customise the headers of the columns of the table which is displayed on the admin page for your custom post type, define a method on your class called `adminColumnHeaders`. This method can accept an array containing the default column headers and should return an array of key value pairs representing the slug and name of the columns respectively.

    public function adminColumnHeaders($defaultColumns)
    {
        return [
            'checkbox' => '<input type="checkbox">',
            'name' => 'Name',
            'content' => 'Content'
        ];
    }


## Registering a custom post type

To load your new custom post type class when the plugin boots, you just need to register the class name in the plugin config files. Add the class name under the `custom_post_types` key in the `config/wordpress.php` config file.


    /*
    |--------------------------------------------------------------------------
    | Registered Custom Post Types
    |--------------------------------------------------------------------------
    |
    | The classes listed here will be automatically loaded on the request to
    | your application to register their corresponding custom post types
    |
    */

    'custom_post_types' => [
        \MyVendor\MyPlugin\CustomPostTypes\MyCustomPostTypeName::class,
    ],
    
Hey presto, your custom post type is good to go!
