---
layout: post
title:      "Ruby iterators"
date:       2020-06-28 19:20:15 +0000
permalink:  ruby_iterators
---


It's been a while since the last time I coded in Ruby, therefore I thought it would be useful to create a simple guide focused on iterators in order to refreash my memory. In Ruby, if you want to iterate over the elements of an array, you have several different methods. In order to use them efficiently, it is important to understand what each of them returns. I therefore decided to make a small cheat sheet for other beginners struggling to read official documentation or going through all the different stackoverflow questions. (These iterators can be used on hashes as well, but for simplicity reasons I will only discuss arrays in this article).

Before I can continue about the iterator methods, I have to mention that another major difference with other programming languages is the implicit return. At first when I started learning Ruby, I kept writing “return” at the end of every method regardless of what was happening in that method. While this does not break the code, it is also not necessary. The last line of a method in Ruby is usually what will be returned. You should therefore only explicitly ask for a return value if you want it to be something else than the last line of code in the method.

The below table shows some of the most popular iterators with their return values:

![](https://miro.medium.com/max/1218/1*iFEHVpjwPOKUZyX_ghxNWQ.png)


![](https://media.giphy.com/media/QsJc1iCW3KfLG5Ol7o/giphy.gif)

