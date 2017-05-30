---
ID: 38
post_title: Admin Menus
author: webspanner
post_date: 2017-05-30 22:25:21
post_excerpt: ""
layout: page
permalink: >
  http://arc-framework.com/documentation/wordpress-api-wrapper/admin-menus/
published: true
---
# Create an admin page under 'Settings' in the wp-admin sidebar

A good place to register admin menus would be in a service provider. Here are the minimum
settings you need to pass in to register an admin menu for your plugin.

```
//&lt;?php

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
        $adminMenus-&gt;createSettingsPage()
            -&gt;whichRendersView(&#039;admin.settings&#039;)
            -&gt;withSettings([
                &#039;my_plugin_some_setting&#039;
            ])-&gt;add();
    }
}

```