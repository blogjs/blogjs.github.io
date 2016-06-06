---
layout: post
comments: true
title:  "Constants in Javascript - Ecmascript 6"
date:   2016-06-06 18:00:00 +0200
categories: javascript ecmascript6 
published: true
tags: 
    - constants
    - const
    - ecmascript 6
    - es6
    - es
    - javascript
    - js
description: "Understanding how does contant variables work in Javascript ecmascript 6. Immutable variables in Javascript"
thumbnail: "/public/const.png"

---

## Const

In Javascript ES5 there is no immutable variables. Everywhere you are defining `var`, even if you need constant data. And actually you cannot be sure if this variable exists or has the proper value after x lines of code executed. \n So in Javascript ES6 there is `const`, like the C++ one, which allows you to have immutable variable, so let's look how does it work:  <!--more-->

___

## Declaration

Very simple. Just use `const` instead of `var` :

    const brandColor = 'turquoise';  

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

___

ES 2015 provided `const` and `let` to let us write `var`-free javascript. So try to figure it out :) 


