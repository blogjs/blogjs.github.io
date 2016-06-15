---
layout: post
comments: true
categories:
    - AngularJS
title:  "Creating AngularJS Directive 'Three-state-checkbox'"
date:   2016-06-16 00:00:00 +0200
published: false
tags: 
    - AngularJS
    - Directive
description: "How to create and export AngularJS directive. Open source project, published on GitHub. How to update scope in angular directive"
thumbnail: "/public/three-state-checkbox.png"
keywords: "Angular directive, three-state checkbox, AngularJS"
thumbnailAlt: "three-state checkbox"

---


## Pre-story

Yesterday at work, I've received a task, which I should be done today _(and I actually did)_. <br/>Simple task to filter table by logical value in one column.

So I had 3 values to filter by: `null`, `true` and `false` _(not filtered, published, unpublished)_.<br/>
I've thought what would be the best visual solution for that... 
I knew, that I don't want to create three-option `select`, like that: 
<select>
    <option selected>not filtered</option>
    <option>published</option>
    <option>unpublished</option>
</select>
(what is actually the fastest solution of that issue) .

But I've decided to make three-state-checkbox. I wanted it to be clean and semantic solution, 
so I've also decided to create at home **open-source package** with AngularJS directory of **three-state-checkbox**.
<!--more-->

___

## Preparing your project for public usage

![npm logo](/public/npm-logo.png "Node package manager")
Init your project with **npm** and if you are registered at __npmjs__ you can publish it to node package manager.<br/>
Read more [how to publish your package](https://docs.npmjs.com/getting-started/publishing-npm-packages).

___

![bower logo](/public/bower-logo.svg "bower")
We use **bower** thought **npm** at our project. But our **gulp** is configured to automatically insert **bower** dependencies to _index.html_ when built. <br/>
Also if you are publishing your first package you don't have to register at bower, and documentation is more understandable: 
[Creating package with **bower**](https://bower.io/docs/creating-packages/)<br/>

[* What is the difference between bower and npm?](http://stackoverflow.com/a/18652918/4450072)


___

## Creating AngularJS Directive

If you want to export your directive for others or to use it in a multiple projects, you should create separate **Angular Module** 
with that directive.

    angular.module("threeStateCheckbox", [])
        .directive("threeStateCheckbox", [ function(){
            return {
                restrict: "A",
                transclude: true,
                require: 'ngModel',
                scope: {
                    'ngChange': "&ngChange",
                    'ngModel': "=ngModel"
                },
                link: function(scope, element, attrs, ngModel){
                    
                }
            };
        }]);
        
Ok now we have our angular **module** and **directive**. <br/>
So to use it in another project, you need to add this _JavaScript_ file to _index.html_ and add `"threeStateCheckbox"` to dependencies of your app module.<br/>
And in my directive `ngModel` is required so usage of it should look like this:

**app.js** :

    angular.module("myApp", ["threeStateCheckbox"])
        .controller("myCtrl",[function(){
            this.checkboxModel = null;
        }]);

**index.html** :
    
    <head>
        <!-- title, etc ... -->
        <link rel="text/css" href="three-state-checkbox.css"/>
    </head>
    <body ng-app="myApp" ng-controller="myCtrl as mc">
    
        <!-- html code ... -->
        
        <span three-state-checkbox ng-model="mc.checkboxModel"></span>
        
        <!-- html code ... -->
        
        <script type="text/javascript src="angular.min.js"></script>
        <script type="text/javascript src="three-state-checkbox.js"></script>
        <script type="text/javascript src="app.js"></script>
    </body>
    
