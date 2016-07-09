---
layout: post
comments: true
categories:
    - ECMAScript6
title:  "Arrow functions in ECMAScript 6"
date:   2016-07-08 08:00:00 +0200
published: true
tags: 
    - ECMAScript6
    - 'Arrow Functions'
description: "Syntax and use case of arrow functions in ECMAScript 6"
thumbnail: "/public/arrow-function.png"
keywords: "Arrow function, ECMAScript 6, es6, syntax"
thumbnailAlt: "ECMAScript 6 arrow function"

---

___

## Syntax

Function with no parameters:
{% highlight javascript %}
    () => { statements } 
{% endhighlight %}

Function with single parameter:
{% highlight javascript %}
    singleParam => { statements }
{% endhighlight %}

Function with one and more parameter:
{% highlight javascript %}
    (param1, param2, …, paramN) => { statements }
{% endhighlight %}
    
Function with simple return statement:
{% highlight javascript %}
    n => n*2
{% endhighlight %}

__How did it look in ECMASript 5?__<!--more-->

Function with no parameters:
{% highlight javascript %}
    function() { statements }
{% endhighlight %}

Function with single parameter:
{% highlight javascript %}
    function( singleParam ) { return statements }
{% endhighlight %}

Function with one and more parameter:
{% highlight javascript %}
    function (param1, param2, …, paramN) { return statements }
{% endhighlight %}
    
Function with simple return statement:
{% highlight javascript %}
    function(n){return n*2}
{% endhighlight %}
    
___

## Use case
I __love the syntax__ of arrow functions in ECMAScript 6! I always asked myself a question *why do I need to write word 
'function' all the time*.
And now I don't have to.

Let's see some examples:
{% highlight javascript %}
    square = n=>n*n;
    square(5); //25
{% endhighlight %}
    
This is simple function that returns square of number passed as a parameter. Isn't it pretty?

In ECMAScript 5 it should be written like this:
{% highlight javascript %}
    function square(n){ return n*n }
{% endhighlight %}
    
But to understand where the new syntax is really helpful, let's look on injected functions:
{% highlight javascript %}
    //ECMAScript 6:
    list.map(item => item*2)
    
    //instead of ECMAScript 5:
    list.map(function(item){return item*2}) 
{% endhighlight %}
{% highlight javascript %}
    //ECMAScript 6:
    { 
        list.forEach(n => {
            if(n>0){
                list2.push(n)
            }
        }) 
    }
    
    //instead of ECMAScript 5:
    (function(){
        list.forEach(function(n){
            if(n>0){
                list2.push(n)
            }            
        })
    }()    
{% endhighlight %}

Don't you see that **ECMAScript 6 is more about program** you wrote, **not about syntax** of it!<br/>

\* In last example in ECMAScript 6 I used a **block-scope**, in ECMAScript 5 only function was block scoped. 
[Read more about block-scope in ECMAScript 6]({% post_url 2016-06-12-es6-block-scoped-functions %})

