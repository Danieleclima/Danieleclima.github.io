---
layout: post
title:      "SQL Data Types"
date:       2020-05-17 21:36:46 +0000
permalink:  sql_data_types
---


It's been a while since I don't touch on SQL, since it's the language that powers the database when coding with Ruby on Rails, I think it deserves a chapter inside my blog :) I'm familiar with SQLite since that's the library I learnt during the bootcamp but I wanted to go further and explore the diferences between SQLite and another very popular library: MySQL.

Now, the biggest difference I can spot right of the bat is Data Types, MySQL is more flexible when it comes to the different types of data it can hold. Here's the list: 

NUMERIC, DATE, DATETIME, TIMESTAMP, NTINYTEXT, BLOB, TEXT, MEDIUMBLOB, MEDIUMTEXT,TIME, YEAR, CHAR, VARCHAR, TINYBLOB, TINYINT, SMALLINT, MEDIUMINT, INT or INTEGER, BIGINT, FLOAT, DOUBLE, DOUBLE DECIMAL, LONGBLOB, LONGTEXT, PRECISION, REAL, ENUM, and SET

Whereas SQLite only supports the following data types: BLOB, REAL, INTEGER, TEXT and NULL. it's worth mentioning that it can support other common data types like INT for example, however it will simply categorize under its "known" catergories (INTEGER in this case). until here everything kind of makes sense, we use REAL to store decimals, INTEGER for numbers and NULL is self-explanatory however the BLOB data type had me a little bit intrigued as I wasn't sure what it purpose was until I decided to learn more about it by googling and reading what others had written before me.

Turns out that BLOB stands for a binary large object that is a collection of binary data stored as a value in the database so basically you can use it  to store the documents, images, and other multimedia files in the database, pretty cool right? According to Wikipedia sometimes binary executable code can also be stored as a blob although Database support is not universal.

As far as Databases and Data types go, these are their building blocks so I'm very excited to continue learning more about them. After all, data is more valuable than gold these days!



