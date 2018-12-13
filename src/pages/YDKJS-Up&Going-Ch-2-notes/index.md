---
title: You Don't Know Javascript Up & Going Chapter 2 notes
date: "2018-12-13"
---

This blog post lists down few notes which i have taken while reading You Don't Know Javascript Part - 1 Up & Going

If either value in a comparison could be true or false USE ===
If either value in a comparison could be one of 0, "" or [] USE ===
For all other cases USE ==

non-primitive values like objects, arrays, functions are stored as references both == and === comparisons will simply check whether references match, not anything about underlying values

arrays are by default coerced to strings by joining all the values with commas in between 

>var a = [1,2,3];
>var b = [1,2,3];
>var c = '1,2,3';

>a == c //true
>b == c //true
>a == b //false

for < comparison, 

if both the values are strings, comparison is made lexicographically,

if one or both is not a string then both values are coerced to numbers

>var a = 41;
>var b = "42";
>var c = "43";

>a < b  //true
>b < c  //true



For > comparison,

> var a = 42;
> var b = "foo";

>a < b //false
>a > b //false
>a == b //false

b gets coerced to NaN, according to specifications NaN is neither greater nor less than any numbers


if a function has a this reference inside it it refers to an object, but which object it refers to depends on how function was called

this DOES NOT REFER TO function itself


>function foo () {
>    console.log(this.bar);
>}

>var bar = 'global'

>var obj1 =  {
>    bar: 'obj1',
>    foo: foo()
>}

>var obj2 = {
>    bar: 'obj2'
>}

>foo() //'global'
obj1.foo() //'obj1'
foo.call(obj2) //'obj2'
new foo() //undefined

foo() ends up setting this to the global object in non-strict mode -- in strict mode, this would be undefined and you'd get an error in accessing the bar property -- so "global" is the value found for this.bar.

obj1.foo() sets this to the obj1 object.

foo.call(obj2) sets this to the obj2 object.

new foo() sets this to a brand new empty object.

javascript prototypes are more of "behavior delegation" pattern

NaN is the only value which is not equal to itself


