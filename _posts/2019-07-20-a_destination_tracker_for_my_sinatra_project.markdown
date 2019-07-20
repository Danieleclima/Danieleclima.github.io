---
layout: post
title:      "A destination tracker for my Sinatra Project"
date:       2019-07-20 16:10:51 +0000
permalink:  a_destination_tracker_for_my_sinatra_project
---


My first goal when I'm thinking about designing a new app is actually building something that is going to add value to people's lives. I'm an avid traveller and in my world it's all about how many countries you have visited so far and also which destinations are you planning to visit next, that's why a destination tracker felt like the right project to improve my Sinatra skills.
On the path towards building my app I faced one major roadblock at the begining which was basically setting up a Linux Local enviroment on my Windows laptop. I first tried installing virtual box and mounting Lubunto onto it, however after many long screenshares with the guys in AAQ and countless attempts to try to make it work I finally found the article that became my absolute life saver. If you are having issues intalling Linux on Windows 10, this [link] (https://github.com/micahshute/wsl-setup) should be your bible, after all the struggle I had before finding it, it took me only a few hours to set up everything following the steps on the guide.
Getting the app working in terms of functionality was my second objective now that I was happily coding on my local enviroment. My idea was to create 3 different models (Country, Trip and User) and give users the ability to have favourite and visited countries and add countries to their bucket list as well. I managed to implement that through creating different columns on my Country class, as you can see below:

```
class CreateCountries < ActiveRecord::Migration
  def change
    create_table :countries do |t|
      t.string :name 
      t.integer :user_id
      t.boolean :favourite_countries 
      t.boolean :visited_countries 
      t.boolean :bucket_list
    end
  end
end
```

This was the easiest way for a user to have many favourite and visited countries and have a list of countries that him/her would like to visit because who doesn't have one of those lists?! my plan is to make the app look prettier once I master my CSS skills which will surely take time, meanwhile is time to continue learning loads on each and every lab!
On to Rails now.

To be continued...



