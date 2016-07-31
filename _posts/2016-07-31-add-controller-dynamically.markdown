---
layout: post
comments: true
categories:
    - AngularJS
title:  "Add AngularJS controller dynamically"
date:   2016-07-31 22:00:00 +0200
published: true
tags: 
    - AngularJS
    - Controller
description: "Adding angular controller dynamically after bootstrapping"
thumbnail: "/public/bootstrapping.png"
keywords: "Controller, AngularJS, add, dynamically, angular, bootstrapping"
thumbnailAlt: "Angular controller bootstrapping"

---

___

Let me show you how to add angular controller dynamically: after application has bootstrapped.
It is useful for example when you are loading components dynamically.

<!--more-->

___

## Inject angular module dynamically (add to dependencies)

A method `.requires.push` allows you to add dynamically another module as dependency to yours.
So, that you will be able to use it's services and directives.<br/>
The syntax is next: 

{% highlight javascript %}
angular.module('mainApp').requires.push('newApp');
{% endhighlight %}

Where the `mainApp` is your main module, and the `newApp` is one you're adding dynamically.

So you get a `mainApp` with dependency of `newApp`:

{% highlight javascript %}
angular.module('mainApp', ['newApp']);
{% endhighlight %}

Ok. With that method you can reach and use all services and directives of `newApp`, but not controllers.

___

## Dynamically add module with controllers

To be able to use **controllers** of **dynamically** added module, you need to register controllers by `$controllerProvider` in your `newApp` you will be adding.
 Here is an example: 
{% highlight javascript %}
angular.module('newApp', [])
    .config(function($controllerProvider) {
        $controllerProvider.register('newAppCtrl', function() {
            // Your Code
        });
    });
angular.module('mainApp').requires.push('newApp');
{% endhighlight %}

___

## Conclusion

**To add new controller dynamically:**

* Create new module and register new controller with `$controllerProvider`
* Add your new module as a dependency dynamically with `.requires.push` method
