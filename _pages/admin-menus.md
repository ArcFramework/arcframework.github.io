---
ID: 38
post_title: Admin Menus
author: webspanner
post_date: 2017-05-30 22:25:21
post_excerpt: ""
layout: page
permalink: >
  http://arc-framework.dev/documentation/wordpress-api-wrapper/admin-menus/
published: true
---
<h1>Create an admin page under 'Settings' in the wp-admin sidebar</h1>

A good place to register admin menus would be in a service provider. Here are the minimum
settings you need to pass in to register an admin menu for your plugin.

<pre><code>//&lt;?php

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

</code></pre>