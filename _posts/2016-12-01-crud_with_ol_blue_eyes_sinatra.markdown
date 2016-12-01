---
layout: post
title:  "CRUD with Ol' Blue Eyes (Sinatra)"
date:   2016-12-01 18:47:14 +0000
---


I* finally* finished my Sinatra App! This particular project was an important milestone for me. I had to really wrap my head around CRUD (**C**reate - **R**ead - **U**pdate - **D**estroy), which was not an easy thing to master. Conceptually, it made sense to me; however, actually building something out was a bit of a challenge. First challenge: creating users. I had to not only allow for someone to create a user account, but I had to ensure that only they could access that account. This required me to use some basic authentication. This involved a few steps. I had to build a database for users that included a username and password (specifically one that could be encrypted). When someone tries to interact with the application, they must enter a username and password. This meant I had to build methods that checked for an empty field and would prevent creating an account if something was left blank. Once a user was created, I had to save that user. Next, to ensure that they could only see their own content, I had to build methods that would match content to users by their IDs. Similarly, I had to build methods (by matching IDs) that would not allow a user to delete or edit someone else's content. While on the subject of editing and deleting, the methods that I built used the unique ID of the specific piece of content that was being interacted with.

For me, the user authentication was the most challenging. I think I have a better understanding of CRUD, but I wouldn't say that I'm an expert yet. There are some things that I built more from rote because I knew that was how it was supposed to be done. Still, I understand way more now than I did a month ago. I think with more practice and research I will understand the things that are still a bit of a mystery to me.
