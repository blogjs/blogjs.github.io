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
description: "Overview of syntax and use case of arrow functions in ECMAScript 6"
thumbnail: "/public/arrow-function.png"
keywords: "Arrow functions, ECMAScript 6, es6, syntax"
thumbnailAlt: "ECMAScript 6 arrow function"

---

___

I think that an **arrow functions** are one of the best features of **ECMAScript 6**, excluding `class`-es and **OOP** programming at all.

It has really very helpful and **useful syntax** for scripting language. So let's check it out:
<!--more-->

___

## Syntax

{% highlight javascript %}
    //Function with no parameters:
    () => { statements } ]

    //Function with single parameter:
    singleParam => { statements }

    //Function with one and more parameter:
    (param1, param2, …, paramN) => { statements }
    
    //Function with simple return statement:
    n => n*2
{% endhighlight %}

__How did it look in ECMASript 5?__

{% highlight javascript %}
    //Function with no parameters:
    function() { statements }

    //Function with single parameter:
    function( singleParam ) { return statements }

    //Function with one and more parameter:
    function (param1, param2, …, paramN) { return statements }
    
    //Function with simple return statement:
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
Read more here: 

+ [Block-scoped functions in ECMAScript 6]({% post_url 2016-06-12-es6-block-scoped-functions %}) 
+ [Block-scoped variables in ECMAScript 6]({% post_url 2016-06-09-es6-let-block-scoped-variables %})

