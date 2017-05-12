# Getting Started

The following are instructions for getting started with creating a plugin using Arc.

## Installation

You can install the plugin in two ways:

1. [Via the installer](#installer)
2. [Via git](#installation-via-git)

### 1) Installer

First, download the Arc installer using Composer:

composer global require "arc-framework/installer"
Make sure to place the $HOME/.composer/vendor/bin directory (or the equivalent directory for your OS) in your $PATH so the 
arc executable can be located by your system.

Use the `arc new` command to generate the boilerplate and install neccessary dependencies for a new plugin built with Arc.

    arc new

The command prompt will guide you through the process, asking for the required informatio (plugin name, slug, namespace etc.)
to avoid the need for any string replacement in the plugin boilerplate. Some sensible defaults will be suggested based on
your chosen plugin name to allow you to get started with minimal effort.

### 2) Clone via Git

To install via git you should clone the `ArcFramework/plugin` repository. This installs the plugin boilerplate with it's
dependencies including the Arc framework. To download the dependencies you will need to run `composer install` after the
repository has been cloned. You will also probably want to remove the `.git` folder and run `git init` to initialise your
own git repository.

## Installing plugin in Wordpress

Once you have your plugin boilerplate setup you will probably want to install the plugin into a local Wordpress installation
for testing purposes while you are developing it. It is generally a good idea to develop your plugin in a separate folder to
your local wordpress installation. You can do this by using a symbolic link to allow Wordpress to find your development 
directory in the `wp-content/plugins` folder. Suppose your plugin was called `my-plugin` and you had installed the development
copy in your `~/Code` directory (`~/Code/my-plugin`), and your wordpress installation was in `~/wp` you should run:

`ln -s ~/Code/my-plugin ~/Code/wp/wp-content/my-plugin`

Your plugin should now be available to activate in the Plugins menu of wp-admin in your Wordpress installation.

## Where do I put my code?

Good question. There are a few different approaches you could try:

### Plugin::run() method

Add a `run()` method to your `Plugin` class which is created in the root `app/` directory when you install the plugin
boilerplate. If it exists, this method will be automatically called when the plugin is booted, and any typehinted parameters
will be automatically injected via the service container.

### Service Providers

You could create service providers which you could use to bind your dependencies and bootstrap components of your plugin.

## Shipping The Plugin

To a produce a shippable zip file of your plugin when it's ready you can use the `php arc ship` command in Arc's 
`artisan`-esque `arc` CLI tool. This will "compile" a zip file of your plugin without dev dependencies and with all files and
directories named in the `.shipignore` file deleted. The file will be named automatically according to the version number you
have named in your main plugin file, so make sure you bump the version number each time you run the command. By default these
files are saved in your home directory with the plugin name as a subdirectory formatte like this: 
`~/plugin-name/plugin-name-1.0.0.zip`. If you wish to customise where the Arc plugins are shipped to you can set a default
with an `~/.arc/config.php` file.

```
<?php

/*
 |---------------------------
 | Arc Framework CLI Config
 |---------------------------
 */
 
return [
    'shippedPluginDirectory' => '/Users/Me/plugins`
];
```
