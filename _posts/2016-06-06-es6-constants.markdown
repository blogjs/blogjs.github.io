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

In **ECMAScript 6** we have **`const`** variable arrived. Does it work the same as C++ `const`? <br/>
Not exactly. I would even say, <i>"not at all"</i>.<br/>
When you declare something with `const` in **ECMAScript 6**, it means that the **identifier can't be reassigned.** <br/>

**What does it mean?** <br/><!--more-->

 - It means that you cannot declare that variable more than once. Because its **binding is immutable**. <br/>
 - You have guaranty that **no rebinding will happen** to it. <br/>
 - You will **not** be able to change its **type**.<br/>
 - If your `const` variable is a simple value, like `string`, `number`, `boolean` etc. you also **wouldn't be able to change its value**.<br/>
 
So let's look how does it work:  

___

## Declaration

Very simple. Just use `const` instead of `var` :

    const brandColor = 'turquoise';  

The value of a constant doesn’t have to to be known at compile time, but you must assign it a value exactly once.

___

## `Const` and scopes

**Redeclaring:**

Constants can’t be redeclared. 

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

You cannot change value or delete a simple constant variable.

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

Use `const` when you don't need reassign the identifier. In practice it is becoming the brand new `var` for **objects** and **arrays**. <br/> 
Because if you need to change type of any of them, it seems you wrote bad, not semantic code.

___

## And what about `let` ?
Read more in the [**LET in ECMAScript 6**]({% post_url 2016-06-09-es6-let-block-scoped-variables %})

___

ES 2015 provided `const` and `let` to let us write `var`-free javascript. So are you going to use `var` again? :) 


