# Installation

You can install the framework in two ways:

1. [Via the installer](#installer)
2. [Via git](#installation-via-git)

## 1) Installer

First, download the Arc installer using Composer:

composer global require "arc-framework/installer"
Make sure to place the $HOME/.composer/vendor/bin directory (or the equivalent directory for your OS) in your $PATH so the 
arc executable can be located by your system.

Use the `arc new` command to generate the boilerplate and install neccessary dependencies for a new plugin built with Arc.

    arc new

The command prompt will guide you through the process, asking for the required informatio (plugin name, slug, namespace etc.)
to avoid the need for any string replacement in the plugin boilerplate. Some sensible defaults will be suggested based on
your chosen plugin name to allow you to get started with minimal effort.

## 2) Clone via Git

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
