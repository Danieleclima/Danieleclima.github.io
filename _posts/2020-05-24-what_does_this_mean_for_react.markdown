---
layout: post
title:      "What does this mean for React?"
date:       2020-05-24 21:00:45 +0000
permalink:  what_does_this_mean_for_react
---


What's this? Sometimes in React it's hard to tell what's what specially when using the keyword this. In Javascript the ‘this’ keyword normally represents a JavaScript element depending on the scope or context of its use, for instance if we are inside the global scope, this should return the Window object. Hence if you open your browser's developer tools and type 'this', the next thing you should see is the Window object like in the below example:

```
//typing this inside the global scope

this

//Will return the Window object

Window {frames: Window, postMessage: ƒ, blur: ƒ, focus: ƒ, …}
```

```
//Any command that you would run on the Window object you can run with ‘this’ in the global scope 

this.location = ‘https://learn.co'
//Is the same as
Window.location = ‘https://learn.co'

```

If we are inside an object's scope, then 'this' will refer to the specific object in question. In React we need our class methods (which are nothing but objects) to have access to this.state and this.props but as I mentioned problem if we were to call this inside of a method then it will represent that same method hence we have a problem here.

Enter the bind method, which gives us a solution to our little scope issue. The bind method attaches an object to a function so that every time the function is called it refers to the bound object, for instance:

```
import React, { Component } from ‘react’;
class App extends Component {
  constructor(props) {
    super(props);
		
		//everytime we call clickFunction(), this will refer to the App instance
		
    this.clickFunction = this.clickFunction.bind(this);
  }
  clickFunction() {
    console.log(this.props.value);
  }
  render() {
    return(
      <div onClick={this.clickFunction}>Click Me!</div>
    );
  }
}
```

Another way, and probably the most efficient, to solve the issue would be using the arrow function. The arrow function introduced in ES6 is a function with the current ‘this’ context already bound to the function which comes in very handy as it saves us a couple lines of code since we don't need to use bind on the constructor method like on the above example, we can simply do this:

```
  clickFunction = () => {
    console.log(this.props.value);
  }
```

And this is it!
