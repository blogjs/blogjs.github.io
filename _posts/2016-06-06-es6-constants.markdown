---
layout: post
comments: true
title:  "Constants in Javascript - Ecmascript 6"
date:   2016-06-06 18:00:00 +0200
categories: javascript ecmascript6 
published: false
tags: 
    - constants
    - const
    - ecmascript 6
    - es6
    - es
    - javascript
description: ""
thumbnail: "/public/const.png"

---


HI. If you are here. It seems you've heard about **Ecmascript 6**, and want to know more.

If we'll check [Wikipedia](https://en.wikipedia.org/wiki/ECMAScript), it says that **Ecmascript** is a _'trademarked scripting-language specification'_.
It means that **ES** - it's a specification or in another words standards of scripting languages, such as **JavaScript**, **ActionScript**, **Jscript**. 
**Ecmascript** it is actually core of that languages, standards they are based at.<!--more-->

___

## Ecmascript 6

Known as **ES6** or **Ecmascript 2015** was finalized in June 2015. There were added renewed syntax to create complexed javascript applications with classes, modules etc.

___

## ES6 code example


**Arrow functions:**

    odds  = evens.map(v => v + 1)
    pairs = evens.map(v => ({ even: v, odd: v + 1 }))
    nums  = evens.map((v, i) => v + i)



**Classes:**

    class Rectangle extends Shape {
        constructor (id, x, y, width, height) {
            super(id, x, y)
            this.width  = width
            this.height = height
         }
    }
    class Circle extends Shape {
        constructor (id, x, y, radius) {
            super(id, x, y)
            this.radius = radius
        }
    }

___

## ES6 vs ES5

Here is very useful website by _Ralf S. Engelschall_, which simply shows new features of ES6 by comparing code with ES5:
[es6-features.org](http://es6-features.org)

___

## Browser support

**Google Chrome** and **Mozilla Firefox** support almost whole functionality of ES6, **Microsoft Edge** also is not doing bad. 
Other browsers have not full support. And as you might guess, **Internet Explorer** does not support Javascript in Ecmascript6.
Here is full browser support table: [kangax.github.io/compat-table/es6/](https://kangax.github.io/compat-table/es6/)

But don't upset! **You can write production ready applications using ES6**. You just need to compile it throught **[Babel](https://babeljs.io/)**
which transforms your code to Javascript in ES5.

___

## Conclusion

No doubt, **Ecmascript 6 is sexy!**
If you haven't tried coding in **Ecmascript 6** just open **Chrome dev tools** and try it out. You will definitely love it!
Start with simple arrow functions:
    
    a = x => x*2;
    a(10);
    
Good luck ;)
