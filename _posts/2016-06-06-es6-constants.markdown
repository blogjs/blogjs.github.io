---
layout: post
comments: true
categories:
    - ECMAScript6
    - Javascript
title:  "Constants in Javascript - ECMAScript 6"
date:   2016-06-06 18:00:00 +0200
published: true
tags: 
    - Const
    - ECMAScript6
description: "Understanding how does constant variables work in Javascript ECMAScript 6. Immutable variables in Javascript"
thumbnail: "/public/const.png"
keywords: "const, ECMAScript 6, ECMAScript 2015, es6, javascript, immutable variables, constant"
thumbnailAlt: "Const ES6"

---

## Const

In Javascript ES5 there is no immutable variables. Everywhere you are defining `var`, even if you need constant data. And actually you cannot be sure if this variable exists or has the proper value after x lines of code executed. 
So in Javascript ES6 `const` variable came. 
When you declare something with `const`, it means that the identifier can't be reassigned. So let's look how does it work:  <!--more-->

___

## Declaration

Very simple. Just use `const` instead of `var` :

    const brandColor = 'turquoise';  

The value of a constant doesn’t have to to be known at compile time, but you must assign it a value exactly once.

___

## `Const` and scopes

**Redeclaring:**

Constants follow the same scope rules as variables but they can’t be redeclared. 

    const num = 1;
    //1
    const num = 2;
    //Uncaught TypeError: Identifier 'num' has already been declared(…)


**Function scope:**

You can declare `const` inside the function scope with the same as outside it, but you actually have local scoped `const`.

    const num = 1;
    
    function setNum(){
        const num = 2;
        console.log(num);
    }
    
    setNum();
    //2;
    
    console.log(num);
    //1;
    
You cannot reach `const` outside scope:

    if(!num){
        const num = 2;
    }
    console.log(num);
    //Uncaught ReferenceError: num is not defined(…)

Ok that's easy. But also you cannot reach const by `this`, because it is block-scoped:
 
    
    const date = new Date();
    
    console.log(this.date);
    //undefined
    
___

## Deleting and changing value of `const`

You cannot change value or delete constant.

    const a = 1;
    
    a++;
    //Uncaught TypeError: Assignment to constant variable.(…)
    
    delete a;
    //true
    
    console.log(a);
    //1

___

## `Const` Objects

If you declare `const` Object, you will not be able to delete it, or make it `array` or `string`, but you will be able to declare, change and even delete values of your `const` Object.

    const params = {
        size: 2,
        color: 'gray'
    }
    
    params = {};
    //Uncaught TypeError: Assignment to constant variable.(…)
    
    params.size++;
    delete params.color;
    
    console.log(params)
    //Object {size: 3}


But there is the way to `freeze` the Object with its values:

    const obj = Object.freeze({
        'num': 3
    });
    obj.num = 4; //throws error
    
___

## So where to use `const` ?

Use `const` when you don't need reassign the identifier. In practice it is becoming the brand new `var`

___

## And what about `let` ?
Read more in the [**LET in ECMAScript 6**]({% post_url 2016-06-09-es6-let-block-scoped-variables %})

___

ES 2015 provided `const` and `let` to let us write `var`-free javascript. So try to figure it out :) 


