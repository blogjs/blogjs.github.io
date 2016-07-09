---
layout: post
comments: true
categories:
    - ECMAScript6
title:  "Block-Scoped Functions in ECMAScript 6"
date:   2016-06-12 19:00:00 +0200
published: true
tags: 
    - Scope
    - ECMAScript6
description: "Understanding Block-Scoped Functions in Javscript ECMAScript 6. Comparsion of block-scoped functions in ES5 vs ES6"
thumbnail: "/public/scopes.png"
keywords: "block scoped functions, ECMAScript 6, JavaScript, block scoping, scope, context"
thumbnailAlt: "Scope"

---

Image above clearly shows how does **scope** is nesting in JavaScript. <br/>
In JavaScript **ECMAScript 5** every scope it is **a scope of function**. Blocks, like `if{}else{}`, are not creating their own scope.

If you want to make your function **block-scoped in ES5** you'll have to **nest** it to another **function**. <br/>
But in **ECMAScript 6** you have better solution!
<!--more-->

This is the way we'd write in **ESCMAScript 5**:

    (function(){
        function privateFunc(){
            console.log("You cannot reach me outside this scope");
            (function(){
                console.log("You cannot reach me even from privateFunc");
            })();
        }
        privateFunc();
    })();
    
    
And here is **ECMAScript 6 block-scoped functions**:

    {
        function privateFunc(){
            console.log("You cannot reach me outside this scope")
            {
                console.log("You cannot reach me even from privateFunc")
            }
        }
        privateFunc()
    }
    
As you see, everything between a curly brackets **`{`** & **`}`**  has own scope in **ECMAScript 6**!