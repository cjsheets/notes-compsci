# Javascript Basics




## Challenges - Javascript



**Question:** Compare null vs undefined.

**Answer:** 

`undefined` is a type, the value of the global undefined variable. You can encounter undefined by:

* declare a variable without assigning a value.
* implicit returns from functions.
* return statements that do not return anything.
* lookup non-existent object properties.
* function parameters that were not passed.

`null` is a primitive value (ie. not an object) that indicates "no value". typeof null === 'object',
but it has no properties and is primative.

-----

**Question:** What are the rules for implicit coerrsion.

**Answer:** 

`undefined` is a type, the value of the global undefined variable. You can encounter undefined by:

* If both operands are same type use ===
* undefined == null
* If string and number, convert string to number
* If boolean and non-boolean, convert boolean to number and compare
* While comparing a string or number to an object, try to convert the object to a primitive type and then try to compare

-----

**Question:** How are objects compared in javascript

**Answer:** 

Primitives are compared by value, objects are compared by reference.


-----

**Question:** What does `this` refer to in javascript

**Answer:** 

`this` is a property set by the Javascript engine which refers to the current execution context. It refers to an object and depends
on how a function is called.

1. In the global context or inside a function this refers to the window object.
2. Inside IIFE (immediate invoking function) if you use "use strict", value of this is undefined. To pass access window inside IIFE with "use strict", you have to pass this.
3. While executing a function in the context of an object, the object becomes the value of this
4. Inside a setTimeout function, the value of this is the window object.
5. If you use a constructor (by using new keyword) to create an object, the value of this will refer to the newly created object.
6. You can set the value of this to any arbitrary object by passing the object as the first parameter of bind, call or apply
7. For dom event handler, value of this would be the element that fired the event

-----

**Question:** Does javascript pass by value or reference

**Answer:** 

Primatives are pass by value, objects are pass by reference. As a result, changing props on an object will affect the original object.
Overwriting the object will simply overwrite the reference being used.



*Sources:*

* [thatjsdude](http://www.thatjsdude.com/interview/js2.html#nullVsUndefined)

let date = new Date()
date.nextDay = () => 
