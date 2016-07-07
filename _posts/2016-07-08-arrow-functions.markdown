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

    //ECMAScript 6:
    () => { statements } 
    
    //ECMAScript 5:
    function() { statements }

Function with single parameter:
    
    //ECMAScript 6:
    singleParam => { statements }
    
    //ECMAScript 5:
    function( singleParam ) { return statements }

Function with one and more parameter:

    //ECMAScript 6:
    (param1, param2, …, paramN) => { statements }
    
    //ECMAScript 5:
    function (param1, param2, …, paramN) { return statements }
    
Function with simple return statement:

    //ECMAScript 6
    n => n*2
    
    //ECMAScript 5
    function(n){return n*2}

___

## Use case
I __love the syntax__ of arrow functions in ECMAScript 6! I always asked myself a question *why do I need to write word 'function' all the time*.
And now I don't have to.

Let's see some examples:

    square = n=>n*n;
    
    square(5); //25
    
In ECMAScript 5 it should be written like this:

    function square(n){ return n*n }
    
But to understand where the new syntax is really helpful, let's look on injected functions:
 
    //ECMAScript 6:
    list.map(item => item*2)
    
    //ECMAScript 5:
    list.map(function(item){return item*2})
    
    //ECMAScript 6
    {
        
    }
    
    //ECMASCript 5:
    (function(){
        
    })()