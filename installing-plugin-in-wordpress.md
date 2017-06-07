# Installing plugin in Wordpress

Once you have your plugin boilerplate setup you will probably want to install the plugin into a local Wordpress installation
for testing purposes while you are developing it. It is generally a good idea to develop your plugin in a separate folder to
your local wordpress installation. You can do this by using a symbolic link to allow Wordpress to find your development 
directory in the `wp-content/plugins` folder. Suppose your plugin was called `my-plugin` and you had installed the development
copy in your `~/Code` directory (`~/Code/my-plugin`). To install via symlink to a Wordpress installation located in `~/Code/wp` you should run:

`ln -s ~/Code/my-plugin ~/Code/wp/wp-content/my-plugin`

Your plugin will now be available to activate in the Plugins menu of wp-admin in your Wordpress installation.
