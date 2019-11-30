---
layout: post
title:      "About Ruby Associations & APIs"
date:       2019-11-30 15:25:22 +0000
permalink:  about_ruby_associations_and_apis
---


My Javascript project has been my most complete app so far, since I've had to demonstrate not only that I was able to code in Ruby and Javascript but also because it was the first project in which I used Bootstrap in order to make my app responsive. Bootstrap is a free and open-source CSS framework directed at responsive, mobile-first front-end web development which is key these days given more people browse on their mobile than on a desktop computer.

Setting up the API was quite straight forward as all I had to do was using a rails generator command followed by the api flag. However, my app was built so that gym goers can find the best gyms in their city and for that I created gym and  location classes, that way a location could have many gyms. The issue was that my app, beign an SPA (single page application) had to be able to fetch all the gyms from the database based on a city name passed by the value of a select HTML tag. At the time, I thought that the best way to achieve that functionality was to create a city_name colum on my database since all I had was a location_id column which didn't expose the property (the city_name) I was after. Below is my database schema:

```
ActiveRecord::Schema.define(version: 2019_11_25_202013) do

  create_table "gyms", force: :cascade do |t|
    t.string "name"
    t.string "rating"
    t.string "openinghours"
    t.datetime "created_at", null: false
    t.datetime "updated_at", null: false
    t.integer "location_id"
    t.string "url"
    t.string "image"
    t.string "city_name"
  end

  create_table "locations", force: :cascade do |t|
    t.string "country"
    t.string "city"
    t.datetime "created_at", null: false
    t.datetime "updated_at", null: false
  end

end
```

I now realize that the best way to approach this issue would have been manipulating the gym objects on my API's controller and adding a city_name key to them. that kind of makes sense in my mind now but a couple of days ago it gave me a headache, which goes to show how much you can learn when you work on an app that requires you to use all the knowledge that you have acquired so far.

This is a very exciting part of the curriculum which is now over, can't wait to start with React!




