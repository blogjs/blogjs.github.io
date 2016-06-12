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
thumbnailAlt: "ECMAScript 6 let"

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
 
## `for` loop
 
 It is really **not clever**, that in **JavaScript ES5** when you create a **variable** in a `for` loop, 
 you can **reach that variable out of that loop**. <br/>
 For example, if you had a **variable** with the **same name** it will be **rewritten** by a variable from inside a `for` loop. 
 
**ECMAScript 5 example**:
 
     var i = 5;
     //...
     for(var i=0; i<10; i++){
        //...
     };
     console.log(i);
     // 10
 
In ES6 this problem solves with `let` variable, because it is **block-scoped**, so our new `let` variable will be scoped to `for` block.
 
 **ECMAScript 6 example**:
  
      let i = 5;
      //...
      for(let i=0; i<10; i++){
         //...
      };
      console.log(i);
      // 5
 
 ___
 
## `let` and `const` best practices
 
 - `const` variable should become your default variable. <i>(Read about [const]({% post_url 2016-06-06-es6-constants %}) to know why)</i>
 - Use `let` for simple variables, which are had to be changed. 
 - It is good to use `let` in `for` loops, because you always need block-scoped variable there
 - Try to exclude `var` from your code. `var` is now the weakest signal available when you define a variable in JavaScript