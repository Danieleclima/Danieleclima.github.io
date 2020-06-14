---
layout: post
title:      "React vs. Plain JavaScript"
date:       2020-06-14 19:36:29 +0000
permalink:  react_vs_plain_javascript
---


So, we’ve looked at the three major ways React is different than plain JS. In particular, those were:

* Plain JS apps usually start with the initial UI created on the server (as HTML), whereas React apps start with a blank HTML page, and dynamically create the initial state in JavaScript.

* React requires you to break your UI into components, but plain JS apps can be structured in any way you see fit.

* Data for plain JS apps are stored in the DOM itself and has to be found from the DOM before it can be used. React apps store data in regular JavaScript variables.

* UI updates in plain JS have to happen by finding the DOM node to update and manually appending or removing elements. React automatically updates the UI based on setting and changing state within the component.
