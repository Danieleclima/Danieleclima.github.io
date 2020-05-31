---
layout: post
title:      "Hoisting in Javascript"
date:       2020-05-31 20:36:38 +0000
permalink:  hoisting_in_javascript
---


I've decided to dedicate my nth Blogpost to one of the most difficult concepts to grasp in my opinion: Hoisting in Javascript. Hoisting can be reffered to as a way of thinking about how execution contexts work in Javascript, or in other words, what's actually going on when you execute your code.

Many people think, including myself not long ago, that Hoisting simply means that variable and function declarations are physically moved to the top of your code. However that's not exactly what happens under the hood, in reality the variable and function declarations are put into memory during the compile phase, which is the phase that comes before runtime.

What putting variables and functions into memory does is that it allows you to call them even before declaring them, like in the example below:

```
function dogName(name) {
  console.log("My doggy name is " + name);
}

catName("Snoop");

/*
The result of the code above is: "My doggy name is Snoop"
*/
```

The above shows how you would normally expect your code to be executed, now let's take a look at what would happen if we were to call the function before we even define it in our code:

```
dogName("Snoop");

function dogName(name) {
  console.log("My doggy name is " + name);
}
/*
The result of the code above is: "My doggy name is Snoop"
*/
```

As you can see we are able to call our dogName function. it's worth mentioning that only declarations are hoisted, not initializations. If a variable is declared and initialized after using it, the value will be undefined, for instance:

```
console.log(truth); // Returns undefined, as only declaration was hoisted, no initialization has happened at this stage 
var truth; // declaration
truth = "Black Lives Matter" // initialization
```


