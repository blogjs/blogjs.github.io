---
layout: post
comments: true
title:  "Ecmascript 6"
date:   2016-05-29 20:00:00 +0200
categories: javascript ecmascript6
published: true
tags: 
    - ecmascript 6
    - es6
    - es
description: "Ecmascript 6 review. Information about ecmascript 6. Differences between ecmascript 5 and ecmascript 6."
thumbnail: "/public/es6.png"

---


HI. If you are here. It seems you've heard about **Ecmascript 6**, and want to know more.

If we'll check [Wikipedia](https://en.wikipedia.org/wiki/ECMAScript), it says that **Ecmascript** is a _'trademarked scripting-language specification'_.
It means that **ES** - it's a specification or in another words standards of scripting languages, such as **JavaScript**, **ActionScript**, **Jscript**. 
**Ecmascript** it is actually core of that languages, standards they are based at.

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
