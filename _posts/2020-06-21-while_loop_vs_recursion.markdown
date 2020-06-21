---
layout: post
title:      "While loop vs Recursion"
date:       2020-06-21 19:06:13 +0000
permalink:  while_loop_vs_recursion
---


This post is about one issue that I faced as I was developing one of my projects. It was a problem that had a relatively easy fix however I kept on hitting a dead end simply becuase my function was stuck in an infinite loop. Also, I was making calls to an external API and therefore I exceeded the call limits several times without getting the chance to debug and see what was causing my function to fail.

Here's the code at the core of my function when I was using the while loop to make calls:

```
        if (response.paging.next) {
          let url = response.paging.next
             while(url){
						 fetch(url)
              .then(res => {
                debugger
                return res.json()
              })
              .then(received_venues => {
                debugger
                received_venues.data.forEach(nightclub => 
                  venues[0].push(nightclub))
                  if(received_venues.paging){
                    return url = received_venues.paging.next
                  } else {
                    return url = undefined
                  }}
              })}
```

In fetching the external API this way, I was making a fata mistake since the url variable would always evaluate to true and therefore my code was destined to be stuck in an eternal loop. Once I saw the issue clearly I decided that the best way to solve the issue was to use Recursion. A recursive function is a function that calls itself until it doesn’t, and that technique known as Recursion. Below is how the previous piece of code would look using Recursion rather than a while loop:

```
        if (response.paging.next) {
          let url = response.paging.next
            let fetchData = function(){ fetch(url)
              .then(res => {
                debugger
                return res.json()
              })
              .then(received_venues => {
                debugger
                received_venues.data.forEach(nightclub => 
                  venues[0].push(nightclub))
                  if(received_venues.paging){
                   url = received_venues.paging.next
                   fetchData()
                  } else {
                  fetchNightClubs(venues)
                  }
              })}
              fetchData()
```

I personally think that my recursive function looks more elegant and works better for when you are trying to fetch external data, so give a try if you are facing the same issue!
