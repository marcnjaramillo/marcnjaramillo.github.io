---
layout: post
title:      "Refining a Recipe - Part 3"
date:       2018-07-23 06:21:04 +0000
permalink:  refining_a_recipe_-_part_3
---


This week was a very busy week. I was asked last minute to go out of town to work a convention happening over the weekend, and I worked 45 hours in 4 days. I'm on my way home, but I am exhausted. For that reason, this will be a shorter post than usual.

## What I Accomolished

This week I worked on two things:

Allow users to upload pictures - this one was a little tricky. I first looked into using the Paperclip gem...until I found out it was deprecated. The documentation directed me to use a  Rails 5 feature known as Active Storage. To do this I had to do some preliminary work first. The first thing that needed to happen was updating Rails in my project. Then I needed to make some changes to files in my project to get it up and running. 

Secure comments - this was a bit easier to take care of. I wanted to make sure that when someone posts a comment only the commentor and recipe owner could delete it. This involved checking for the user id and matching it to either the commentor or the recipe owner.

## Next Update

Now I will be working on the categories feature. Stay tuned!
