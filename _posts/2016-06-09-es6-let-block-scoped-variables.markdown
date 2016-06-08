---
layout: post
comments: true
categories:
    - ECMAScript6
    - Javascript
title:  "LET in ECMAScript 6 - Block Scoped Variables"
date:   2016-06-09 1:00:00 +0200
published: true
tags: 
    - Let
    - Scope
    - ECMAScript6
description: "Understanding let in Javascript ECMAScript 6. Difference and comparsion of let and var. Block scoped variables in es6."
thumbnail: "/public/letitbe.jpg"
keywords: "let, var, block scoped variable, ECMAScript 6, javascript"

---

**`let`** has the same block scoping as [`const`]({% post_url 2016-06-06-es6-constants %}), but let us look over **Block Scoped Variables** in **ECMAScript 6**

<!--more-->

___

## Understanding Block Scope

Let's compare `var` and `let` behavior with `this`: 

    var x = 'global';
    let y = 'global';
    console.log(this.x); //'global'
    console.log(this.y); //undefined
    
It looks like `let` variable has its own scope.

  
    if(1>0){
        var x = 0; //scope is inside the function
        let y = 1; //scope is inside the if-block
    }
    console.log('x:', x); //0
    console.log('y:', y); //undefined
    
As you can see, `var` scope is inside the function and `let` scope is inside if-block.

___

**Why does it happen?**
 
 Because when you write code like this: 
 
    function a(){
        if(true){
            var b = 1;
        }
    }
    
 The really thing Javascript doing is :
 
    function a(){
        var b;
        if(true){
            b = 1;
        }
    }
    
 But when you use `let` or `const` it looks another way.
 
 This code:
 
    function a(){
        let b = 0;
        if(true){
            let b = 1;
        }
     }
     
 Becomes this:
 
    function a(){
        var b = 1;
        if(true){
            var b$0 = 1;
        }
     }
     
 ___
 
## `let` and `const` best practices
 
 - `const` variable should become your default (immutable) variable. 
 - Use `let` if you need to provide changes to your variable. 
 - It is good to use `let` in `for` loops, because you always need block-scoped variable there:
 
        for(let i = 0; i<5; i++){
            console.log(i)
        }
- Try to exclude `var` from your code. `var` is now the weakest signal available when you define a variable in JavaScript