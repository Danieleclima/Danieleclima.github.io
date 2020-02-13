---
layout: post
title:      "Houston: We've got a CORS problem"
date:       2020-02-13 15:36:10 -0500
permalink:  houston_weve_got_a_cors_problem
---


I made it! I'm here writing the blogpost corresponding to my final project. When I look back at all the roadblocks, setbacks and moments of desperation when I couldn't think clearly and felt like I didn't even know what a computer was, one acronism stands out among the rest of the issues: CORS, which stands for Cross-Origin Resource Sharing.
Given my application needed to make calls to the Google Places API in order to get data from different venues based on a user location, I needed to use the fetch method on my frontend React-Redux app in order to make GET requests both to external and my own Rails API.

In theory, setting this up should have been pretty straight forward but CORS got in the way. It all started when I was trying to get the venue information from the Google Places API using fetch, I was getting nothing back, actually the promise wouldn't even hit any of the .then methods which I thought was pretty strange. Little did I know back then that all of this was happening due to a mechanism that uses additional HTTP headers to tell browsers to give a web application running at one origin, access to selected resources from a different origin. A web application executes a cross-origin HTTP request when it requests a resource that has a different origin (domain, protocol, or port) from its own, which is exactly what I was trying to do in my code below:

```
export function fetchNightClubs(coords) {
    return (dispatch) => {
        if (coords){
        dispatch ({type: 'START_ADDING_NIGHTCLUBS_REQUEST'});
        let proxyUrl = 'https://cors-anywhere.herokuapp.com/';
        let targetUrl = `https://maps.googleapis.com/maps/api/place/nearbysearch/json?location=${coords.latitude},${coords.longitude}&radius=20000&type=night_club&key=`
        fetch(proxyUrl + targetUrl)
        .then(res => {
            return res.json()
          })
        .then(nightclubs => dispatch({type: 'ADD_NIGHTCLUBS', nightclubs: nightclubs.results})) 
        // .catch(error => {
        // 
        //     console.log(error)
        // })  
    }}
}
```


After doing a lot of debugging and googling "how to make CORS requests using fetch" quite a few times, I ran into this article in Stackoverflow which basically offered a solution for my problem, I did rejoice when I saw that it required a relatively easy implementation since all I needed to do was to create the above `proxyUrl` variable and concatenate it to my target URL. it all worked out and although I still don't think this is the ideal solution, I managed to get unstuck which was a huge relief and I've now learned that coding is a journey more than a destination that you need to get to, so I'm sure that sooner than later I will find the optimal solution.

What matters the most to me is that I've finished my final project! so now a new phase begins which I am quite excited about.

God bless Rails, React and Redux. Thank you Flatiron!
