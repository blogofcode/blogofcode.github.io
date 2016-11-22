---
layout:     post
title:      Material Design Web UI Frameworks
date:       2016-11-22 12:31:19
summary:    Created and designed by Google, Material Design is a design language that combines the classic principles of successful design along with innovation and technology. Google's goal is to develop a system of design that allows for a unified user experience across all their products on any platform.
categories: jekyll pixyll
author:     A SAI RAHUL
permalink:  /material-design-web-ui-frameworks/
tags:
  - web-tag
---

![desk](https://raw.githubusercontent.com/blogofcode/blogofcode.github.io/master/images/slide-out-slidebar-menu/Simulator%20Screen%20Shot%20Oct%2025%2C%202016%2C%2010.31.12%20PM.png)

In this post, I would be doing a roundup of some of the third-party(not from Google) Material Design Web UIframeworks that bring Material design to the Web user interface.

Here I would just be discussing how to get started with these frameworks and you can further go deep with their components, templates, etc,.

### [Material Design Lite](https://getmdl.io)

Material Design Lite lets you add a Material Design look and feel to your websites. It doesn’t rely on any JavaScript frameworks and aims to optimize for cross-device use, gracefully degrade in older browsers, and offer an experience that is immediately accessible.

Just add the following `<link>` and `<script>` elements into your HTML pages (27kB gzipped):

{% highlight html %}
    <link rel="stylesheet" href="https://fonts.googleapis.com/icon?family=Material+Icons">
    <link rel="stylesheet" href="https://code.getmdl.io/1.2.1/material.indigo-pink.min.css">
    <script defer src="https://code.getmdl.io/1.2.1/material.min.js"></script>
{% endhighlight %}

And using `Button` component as follows:

{% highlight html %}
<html>
<head>
    <link rel="stylesheet" href="https://fonts.googleapis.com/icon?family=Material+Icons">
    <link rel="stylesheet" href="https://code.getmdl.io/1.2.1/material.indigo-pink.min.css">
    <script defer src="https://code.getmdl.io/1.2.1/material.min.js"></script>
</head>

<body>
    <!-- Accent-colored raised button with ripple -->
    <button class="mdl-button mdl-js-button mdl-button--raised mdl-js-ripple-effect mdl-button--accent">
      Button
    </button>

</body>
</html>
{% endhighlight %}

You can get to their [docs](https://getmdl.io/components/index.html) and explore further.

### [Materialize](http://materializecss.com)

Materialize is a modern responsive front-end framework based on Material Design. For use in your web projects, it provides an option of both CSS as well as source SCSS files, along with JavaScript, material design icons and Roboto font. Included components are basic ones such as grids, forms, buttons, navbar and cards. Materialize is available on [GitHub](https://github.com/Dogfalo/materialize) as well.

Same as above, just add the following `<link>` and `<script>` elements into your HTML pages:

{% highlight html %}
  <!-- Compiled and minified CSS -->
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/materialize/0.97.8/css/materialize.min.css">
  <!-- Compiled and minified JavaScript -->
  <script src="https://cdnjs.cloudflare.com/ajax/libs/materialize/0.97.8/js/materialize.min.js"></script>
{% endhighlight %}

And using `Button` component as follows:

{% highlight html %}
<!DOCTYPE html>
<html>
<head>
    <!-- Compiled and minified CSS -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/materialize/0.97.8/css/materialize.min.css">
    <!-- Compiled and minified JavaScript -->
    <script src="https://cdnjs.cloudflare.com/ajax/libs/materialize/0.97.8/js/materialize.min.js"></script>
</head>

<body>
    <a class="waves-effect waves-light btn">button</a>
    <a class="waves-effect waves-light btn"><i class="material-icons left">cloud</i>button</a>
    <a class="waves-effect waves-light btn"><i class="material-icons right">cloud</i>button</a>
</body>
</html>
{% endhighlight %}

You can further explore their [docs](http://materializecss.com/buttons.html).


### [Material-UI](http://www.material-ui.com/#/)

A Set of React Components that Implement Google's Material Design

This framework depends on `React`. So if you are familiar with `React` go ahead with this framework, if not I recommend you to use above two or you get to know [React](https://facebook.github.io/react/) before diving into Material-UI. Material-UI is a set of React components, so understanding how React fits into web development is important.

I would discussing `Material-UI` along with basics of `React` in the future posts. 

Hope this helps you to build beautiful UI.

Happy Coding :)


---
