---
layout: post
title:      "Portfolio project: Building an IMDB scraper"
date:       2019-05-07 12:08:08 +0000
permalink:  portfolio_project_building_an_imdb_scraper
---


Have you ever been laying on your sofa doing nothing and thought that was the perfect moment to start watching a movie? I have, and in many occasions getting to the conclussion that watching a movie was the right thing to do was just the begining, the tought part came when I had to decide what movie was the best one to watch. I decided to focus my first portfolio project on solving that problem.

If you have not been outside of this world for the past ten years, you are probably familiar with IMDB or have visited their site plenty of times already, but in case you are a martian reading my post, I'm more than happy to let you know that IMDB is the world's most popular and authoritative source for movie, TV and celebrity content where you can find ratings and reviews for the newest movies and TV shows, sounds like the ideal place to look for a movie to watch right? That's what I thought too.

Since my first project had to be based on a CLI data gem, building a movie guide to show the most popular movies made perfect sense. My first concern was figuring out if the IMDB site was going to be easy to scrape at all, luckily getting the different movie titles, years and URLs was not hard to achieve. below you can see the method I used for that purpose:

```
  def self.scrape_popular_movies (index_url)
    doc = Nokogiri::HTML(open(index_url))
    array = []
    doc.css("tbody.lister-list td.titleColumn").each do |movie|
      new_movie = {}
      movie_title = movie.css("a").children.text
      movie_year = movie.css("span.secondaryInfo").children.text[1..4]
      movie_url = movie.css("a").attribute("href").value
      new_movie[:title] = movie_title
      new_movie[:year] = movie_year
      new_movie[:url] = "https://www.imdb.com" + movie.css("a").attribute("href").text
      array << new_movie
    end
    array
  end
```

I placed the above method under my scraper class, however this would only scrape the page where all the movies are sorted by popularity, If I wanted to get additional attributes like the genre or the summary for each of the movies I would have to scrape each of the movie pages separetely and then create a method on my movie class in order to add movie attributes based on a hash, then the next step would be to link every movie object created with the scrape_popular_movies method described before with its respective attributes, to accomplish that I came up with the  following:

```
  def add_attributes_to_movies
    Movie.all.each do |movie|
      attributes = MovieScraper.scrape_movie_page(movie.url)
      movie.add_movie_attributes(attributes)
    end
  end
```

Once I had rationalized how my project was supposed to work in my mind and my Movie and Scraper class were built, it was time for me to create the command line interface class. My CLI class is responsible for calling the above method every time that the movie guide is initiated in order to get an updated list with all the popular movies and also it gets the user input and display the information accordingly based on the user's answer.

That's basically what I had to do (in a nutsell) in order to implement my first project, to give you an idea of what my gem does, I've pasted the cli menu below:

**Welcome to your movie guide!
To list the most popular movies sorted by popularity , enter 'list movies'.
To view the summary of a particular movie, type its index number
To list all of the movies currently showing at the cinema, enter 'what's on'.
To list all the movie genres alphabetically, enter 'list genres'.
To list all of the movies for a particular genre, type the name of the genre.
To view a list of the top upcoming movies, type 'coming soon'
To quit, type 'exit'.
What would you like to do?**

Happy coding!


