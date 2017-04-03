---
layout: post
title: Getting Started wtih Arc
---

# Getting Started

The following are instructions for getting started with creating a plugin using Arc.

## Installation

You can install the plugin in two ways:

1) (Via the installer)[#installer]
2) (Via git) [#installation via git]

### Installer

First, download the Arc installer using Composer:

composer global require "arc-framework/installer"
Make sure to place the $HOME/.composer/vendor/bin directory (or the equivalent directory for your OS) in your $PATH so the 
arc executable can be located by your system.

Once installed, the `arc new` command will create a fresh Arc installation in the directory you specify. For instance, `arc 
new my-plugin` will create a directory named `my-plugin` containing a fresh Laravel installation with all of Arc's 
dependencies already installed:

    arc new my-plugin
    
### Installation via Git

To install via git you should clone the `ArcFramework/plugin` repository. This installs the plugin boilerplate with it's
dependencies including the Arc framework.

