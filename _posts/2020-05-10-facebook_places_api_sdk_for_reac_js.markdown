---
layout: post
title:      "Facebook Places API: SDK for Reac.js "
date:       2020-05-10 20:01:22 +0000
permalink:  facebook_places_api_sdk_for_reac_js
---


If you are ever trying to build a location-aware app then you'll realize that you are probably going to need 3rd party data, at least to get things up and running at the begining, if you really want to get accurate information about restaurants, venues, shopping centers and whatnot. That's when the Facebook places API comes in, making it relatively easy for you to pull out that sort of information from it.

The Facebook Places API stands out from the rest since is completely free to use (T&Cs and limits apply) although the data you get is not categorized in the best way possible which is not the case on the Google or Foursquare API for instansce, so you would have to create some sort of algorithim if you want to filter out a very generic category like Food and Beverage for example.

Since I'm building an app on React.js I wanted to figure out how to make calls using that language. Turns out I needed an SDK which stands for “Software Development Kit” and basically functions providing a set of tools, libraries, relevant documentation, code samples, processes, and or guides that allow developers to create software applications on a specific platform. If an API is a set of building blocks that allow for the creation of something, an SDK is a full-fledged workshop, facilitating creation far outside the scopes of what an API would allow. There's not an specific Reac.js SDK for the Facebook API however there's one for Javascript so I pasted the below code on my index.html file:

```
  <script>
    window.fbAsyncInit = function () {
      FB.init({
        appId: 'Your Facebook App ID',
        autoLogAppEvents: true,
        xfbml: true,
        version: 'v7.0'
      });
    };
  </script>
  <script async defer src="https://connect.facebook.net/en_US/sdk.js"></script>
	
```

The above script will allow you to make calls to the API using a set of methods that Facebook has created for that purpose, here's an example:

```
 init = () => window.FB.api('/search?type=place&q=Mcdonals', {fields: 'name,checkins,website'}, {  access_token : 'Your Access token' }, function(response) {
        console.log(response);
      })
```

that call would console log all the Mcdonal's  restaurants available, if you need to show all the Mcdonal's near a given location then you would have to use coordinates and a radius.


