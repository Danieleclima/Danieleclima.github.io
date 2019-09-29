---
layout: post
title:      "automagic coding with Ruby on Rails"
date:       2019-09-29 10:27:17 -0400
permalink:  automagic_coding_with_ruby_on_rails
---


It wasn't until I started working on my Rails project that I truly realised the power of using Ruby gems for some functionalities when building an app from scratch. This is, in my opinion, what makes Ruby a very collaborative coding language since you can take advantage of what smarter people have created and save loads of time in doing so. Since I'm a foodie, I decided to create a restaurants reviews app for my rails final project.
I really think that reviews are more important than ever nowdays and can have a significant impact on people's decissions so I decided that my app should circle around my reviews model:

```
ActiveRecord::Schema.define(version: 2019_09_14_141216) do

  create_table "categories", force: :cascade do |t|
    t.text "name"
    t.integer "user_id"
    t.integer "restaurant_id"
    t.datetime "created_at", null: false
    t.datetime "updated_at", null: false
  end

  create_table "restaurants", force: :cascade do |t|
    t.text "name"
    t.text "description"
    t.text "category"
    t.text "address"
    t.datetime "created_at", null: false
    t.datetime "updated_at", null: false
  end

  create_table "reviews", force: :cascade do |t|
    t.integer "rating"
    t.datetime "date"
    t.text "description"
    t.integer "user_id"
    t.datetime "created_at", null: false
    t.datetime "updated_at", null: false
    t.integer "restaurant_id"
  end

  create_table "users", force: :cascade do |t|
    t.text "username"
    t.text "password_digest"
    t.datetime "created_at", null: false
    t.datetime "updated_at", null: false
  end

end

```

As you can see on the above database schema, the review model acted as the joint table between my restaurant and user models, therefore Restaurant `has_many :users, through: :reviews` and User `has_many :restaurants, through: :reviews`.
The automagic came (apart from when I used Rails generators) when I used the Omniauth gem to implement social media login. Omniauth standardizes multi-provider authentication for web applications so I was able to have my users loging in via Facebook in just a few hours, which would have taken a lot more time if it wasn't for Omniauth. As I was developing my app I learnt, thanks to other colleagues, that Omiauth was not really compatible with the rails default server called Puma given it requires a https protocol, hence I had to install another gem called thin which provided the https protocol that satisfies OAuth.
I figured out, only after I finished my project unfortunately, that there's another very useful gem which I could have used in order to seed my database called Faker, I had trouble seeding my database so I will keep that in mind for next time. All of the above was made possible thanks to gems!! now I'm moving on to the Javascript section of the curriculum but I'll sure miss the language that introduced me to software engineering. See you later Rails!

![](http://i.imgur.com/6ipUqve.gif)


