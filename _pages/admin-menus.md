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

```
&lt;?php

// Instantiate the admin menus object
$adminMenus = $this-&gt;app-&gt;make(\Arc\AdminMenus\AdminMenus::class);

// Create the settings page
$adminMenus-&gt;createSettingsPage()
    -&gt;called(&#039;My Plugin Settings&#039;)
    -&gt;withMenuTitle(&#039;My Plugin&#039;)
    -&gt;restrictedToCapability(&#039;administrator&#039;)
    -&gt;withSlug(&#039;my-settings-page&#039;)
    -&gt;whichRendersView(&#039;admin.settings&#039;)
    -&gt;withSettings([
        &#039;my_plugin_enable_plugin&#039;

    ])
    -&gt;add();
```