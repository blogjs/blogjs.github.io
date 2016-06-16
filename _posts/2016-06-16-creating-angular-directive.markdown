---
layout: post
comments: true
categories:
    - AngularJS
title:  "Creating AngularJS Directive 'Three-state-checkbox'"
date:   2016-06-16 08:00:00 +0200
published: true
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
        
Ok now we have our angular **module** and **directive** initialized. <br/>
So to use it in another project, you need to add this _JavaScript_ file to _index.html_ and add `"threeStateCheckbox"` to dependencies of your app module.<br/>
In my directive `ngModel` is required so usage of it should look like this:

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
    
Ok. But directive will show nothing now.

If you are creating simple element directive _(like checkbox, input, etc )_, you should better not create template for your directive, but use element, 
by which your directive was initialized in _html_ file. 

Modify your element and then do `$compile(element)(scope);`. 

    
    link: function(scope, element, attrs, ngModel){
        scope.click = function(){};
        element.attr("class", "tri-sta-che");
        element.attr("ng-click", "click()");
        element.removeAttr("three-state-checkbox");
        $compile(element)(scope);        
    }

So as you can see, I've added `ng-click` attribute thought `class` and removed `three-state-checkbox`, because my directive configured with `restrict: "A"` which means it can be linked only by attribute. 

Ok now we need to change `ngModel`, when someone will **click** on the "checkbox". <br/>
4-th attribute of `link` function is _Collection_ of required directives, or single directive, if only one directive is requiired. <br/>
As `ngModel` is the only directive **required** by  **three-state-checkbox** I can reach the `ngModel` object from link function attributes.<br/> 
We will use 2 methods and 1 parameter of `ngModel` object:

* `$setViewValue()` - to set value to `ngModel`
* `$render()` - to render `ngModel` and trigger event for `ng-change`
* `$modelValue` - current value of `ngModel`

<br/>

        link: function(scope, element, attrs, ngModel){
            var states = [true, false, null];
            
            scope.click = function(){
                var st;
                states.map(function(val, i){
                    if(scope.ngModel === val){
                        st = states[(i+1)%3];
                    }
                });
                ngModel.$setViewValue(st);
                ngModel.$render();
            };
            element.attr("class", "tri-sta-che");
            element.attr("ng-click", "click()");
            element.removeAttr("three-state-checkbox");
            $compile(element)(scope);
        }

Ok. Now **three-state-checkbox** directive is working properly, changing **ngModel** and triggering **ngChange** event. 

I've also added `options` parameter to directive, and `ng-class` attribute to element, to change class when state is changed. 

So my first stable version **v 1.0.7** looks like this: 

    'use strict';
    angular.module("threeStateCheckbox", [])
        .directive("threeStateCheckbox", ['$compile', function($compile){
            var dirObj = {
                restrict: "A",
                transclude: true,
                require: 'ngModel',
                scope: {
                    'options': "@options",
                },
                template:'<span class="tsc-b tsc-b-t"></span>'+
                '<span class="tsc-b tsc-b-l"></span>'+
                '<span class="tsc-b tsc-b-r"></span>'+
                '<span class="tsc-b tsc-b-b"></span>',
                link: function(scope, element, attrs, ngModel){
                    config.set(scope.options);
                    var states = [true, false, null];
                    var classNames = ["checked", "unchecked", "clear"];
                    scope.click = function(){
                        var st;
                        states.map(function(val, i){
                            if(ngModel.$modelValue === val){
                                st = states[(i+1)%3];
                            }
                        });
                        ngModel.$setViewValue(st);
                        ngModel.$render();
                    };
                    scope.tscClassName = function(){
                        var className;
                        states.map(function(val, i){
                            if(ngModel.$modelValue=== val){
                                className = classNames[i];
                            }
                        });
                        return className;
                    };
                    element.attr("class", "tri-sta-che " + config.opts.size);
                    element.attr("ng-click", "click()");
                    element.attr("ng-class", "tscClassName()");
                    element.removeAttr("three-state-checkbox");
                    element.removeAttr("options");
                    $compile(element)(scope);
                }
            };
            var config = {
                opts: {
                    size: 'md'
                },
                set: function(options){
                    if(options){
                        for(var key in options){
                            this.opts[key] = options[key];
                        }
                    }
                }
            };
            return dirObj;
        }]);

I've created animations for changing states and **Internet Explorer** doesn't support all styles for _css pseudo-elements_, so I had to create **template** with _spans_.

___

## Versioning

Use **Git tags** to support versioning of your project. Read more about [Git Tagging](https://git-scm.com/book/en/v2/Git-Basics-Tagging)
        
___

## GitHub repository

![GitHub logo](/public/github.png "GitHub") 
[Three-state checkbox - GitHub repository](https://github.com/antontemchenko/three-state-checkbox)

I also need help to extend this directive, so if you want to contribute, I will be very thankful.

___

## Demo 

You can try demo here: [Three-state checkbox DEMO](http://anton.temchenko.com.ua/dev/three-state-checkbox/demo)