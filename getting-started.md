# Getting Started

The following are instructions for getting started with creating a plugin using Arc.

## Installation

You can install the plugin in two ways:

1. [Via the installer](#installer)
2. [Via git](#installation-via-git)

### Installer

First, download the Arc installer using Composer:

composer global require "arc-framework/installer"
Make sure to place the $HOME/.composer/vendor/bin directory (or the equivalent directory for your OS) in your $PATH so the 
arc executable can be located by your system.

Use the `arc new` command to generate the boilerplate and install neccessary dependencies for a new plugin built with Arc.

    arc new

The command prompt will guide you through the process, asking for the required informatio (plugin name, slug, namespace etc.)
to avoid the need for any string replacement in the plugin boilerplate. Some sensible defaults will be suggested based on
your chosen plugin name to allow you to get started with minimal effort.

### Installation via Git

To install via git you should clone the `ArcFramework/plugin` repository. This installs the plugin boilerplate with it's
dependencies including the Arc framework.

## Where do I put my code?

Good question. There are a few different approaches you could try:

### Plugin::run() method

Add a `run()` method to your `Plugin` class which is created in the root `app/` directory when you install the plugin
boilerplate. If it exists, this method will be automatically called when the plugin is booted, and any typehinted parameters
will be automatically injected via the service container.

### Service Providers

You could create service providers which you could use to bind your dependencies and bootstrap components of your plugin.
