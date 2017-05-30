---
ID: 23
post_title: Documentation
author: webspanner
post_date: 2017-05-30 22:02:12
post_excerpt: ""
layout: page
permalink: http://arc-framework.com/documentation/
published: true
---
# Documentation

## Contents

1. [About Arc](#about-arc)
1. [Key Features](#key-features)
1. [Getting Started](getting-started)
1. [Controllers](controllers)
1. [Models](models)
1. [Arc CLI](arc-cli)
1. Wordpress API Wrapper
1. [Hooks](hooks)

### About Arc

Arc was designed to make the development workflow for wordpress plugins as robust and easy as possible for the modern PHP
developer. Arc is built on the shoulders of the popular (Laravel Framework)[laravel.com] for PHP which for many has made leaps
bounds for the developer-friendliness of developing web applications with PHP. Special mention should also go to the
[Symfony Framework](symfony.com) some components of which have been used by Laravel and therefore Arc. This project makes no
apologies for it's inspiration by and emulation of Laravel.

Arc may not be the best solution for every plugin. For example, many plugins could be implemented with a few lines of
procedural PHP in the main plugin .php file. Alternatively, plugins may need to be able to work in a variety of different
server environments or with minimal risk of dependency collisions. If this is your use case, stadard wordpress plugin
development processes might be more efficient, and there's nothing wrong with that approach. Where Arc can shine is for more
complex custom plugin development which relies on depencies pulled in from Composer, and for which testability is essential.

### Key Features

Here are some of the key features of Arc:

#### Composer

Like most modern PHP applications Arc uses [composer](https://getcomposer.org/) for it's dependency managment and autoloading.
No more relentless tangle of `include` and `require` calls!

#### Illuminate IoC Container

Laravel's [Illuminate IoC container](https://laravel.com/master/5.4/container) is perhaps the most fundamental component of
Laravel, and of Arc. In the words of the
Laravel documentation:

&gt; The Laravel service container is a powerful tool for managing class dependencies and performing dependency injection.

#### Illuminate Routing and HTTP Layer

Arc includes Laravel's [Illuminate Routing and HTTP](https://laravel.com/docs/master/routing) components to make an
MVC application flow a breeze with your Arc plugin.

#### Testability out of the box

Arc aims to be fully configured for unit testing with PHPUnit out of the box. Wordpress Doesn't make this very easy, so we've
included a test case out of the box. The Arc test case has a list of helper methods and assertions which cover most of
Laravel's own TestCase API as well as some extra Wordpress specific testing helpers to make this as painless as possible.

#### Eloquent ORM

Arc include's Laravel's [Eloquent ORM](https://laravel.com/docs/master/eloquent) which makes any database operations
very easy.