---
ID: 5
post_title: 'Arc WordPress Plugin Framework &#8211; Documentation Home'
author: webspanner
post_date: 2017-05-27 02:54:21
post_excerpt: ""
layout: post
permalink: >
  http://arc-framework.com/2017/05/27/arc-wordpress-plugin-framework-documentation-home/
published: true
---
<h1>Arc Wordpress Plugin Framework</h1>

<h2>Contents</h2>

<ol>
<li><a href="#about-arc">About Arc</a></li>
<li><a href="#key-features">Key Features</a></li>
<li><a href="getting-started">Getting Started</a></li>
<li><a href="controllers">Controllers</a></li>
<li><a href="models">Models</a></li>
<li><a href="arc-cli">Arc CLI</a></li>
<li>Wordpress API Wrapper</li>
<li><a href="hooks">Hooks</a></li>
</ol>

<h3>About Arc</h3>

Arc was designed to make the development workflow for wordpress plugins as robust and easy as possible for the modern PHP
developer. Arc is built on the shoulders of the popular (Laravel Framework)[laravel.com] for PHP which for many has made leaps
bounds for the developer-friendliness of developing web applications with PHP. Special mention should also go to the
<a href="symfony.com">Symfony Framework</a> some components of which have been used by Laravel and therefore Arc. This project makes no
apologies for it's inspiration by and emulation of Laravel.

Arc may not be the best solution for every plugin. For example, many plugins could be implemented with a few lines of
procedural PHP in the main plugin .php file. Alternatively, plugins may need to be able to work in a variety of different
server environments or with minimal risk of dependency collisions. If this is your use case, stadard wordpress plugin
development processes might be more efficient, and there's nothing wrong with that approach. Where Arc can shine is for more
complex custom plugin development which relies on depencies pulled in from Composer, and for which testability is essential.

<h3>Key Features</h3>

Here are some of the key features of Arc:

<h4>Composer</h4>

Like most modern PHP applications Arc uses <a href="https://getcomposer.org/">composer</a> for it's dependency managment and autoloading.
No more relentless tangle of <code>include</code> and <code>require</code> calls!

<h4>Illuminate IoC Container</h4>

Laravel's <a href="https://laravel.com/master/5.4/container">Illuminate IoC container</a> is perhaps the most fundamental component of
Laravel, and of Arc. In the words of the
Laravel documentation:

<blockquote>
  The Laravel service container is a powerful tool for managing class dependencies and performing dependency injection.
</blockquote>

<h4>Illuminate Routing and HTTP Layer</h4>

Arc includes Laravel's <a href="https://laravel.com/docs/master/routing">Illuminate Routing and HTTP</a> components to make an
MVC application flow a breeze with your Arc plugin.

<h4>Testability out of the box</h4>

Arc aims to be fully configured for unit testing with PHPUnit out of the box. Wordpress Doesn't make this very easy, so we've
included a test case out of the box. The Arc test case has a list of helper methods and assertions which cover most of
Laravel's own TestCase API as well as some extra Wordpress specific testing helpers to make this as painless as possible.

<h4>Eloquent ORM</h4>

Arc include's Laravel's <a href="https://laravel.com/docs/master/eloquent">Eloquent ORM</a> which makes any database operations
very easy.