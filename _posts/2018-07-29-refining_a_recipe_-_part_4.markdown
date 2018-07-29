---
layout: post
title:      "Refining a Recipe - Part 4"
date:       2018-07-29 06:40:26 +0000
permalink:  refining_a_recipe_-_part_4
---


Despite a whirlwhind weekend of working for 43 hours and getting almost no sleep...

![](https://media.giphy.com/media/LTYT5GTIiAMBa/giphy.gif)

I was able to get back into my routine and get things done! With each week I get closer and closer to having my project where I want it to be. I made some pretty significant changes to the styling and I figured out how to enable users to add categories to their recipes. Let me break down how it all came together this week.

## Gotta Keep 'Em Separated

To incorporate categories into my project I decided to do a little hunting on Google to see how other people approached it. It seems that a popular pattern is to create a Category model that `has_many` of a different model. So in my case, it would be my Recipe model that `belongs_to` the Category. The only problem with this approach is that my Recipe model already has that assocation set up with the User model. According to the [Active Record documentation](https://guides.rubyonrails.org/association_basics.html#polymorphic-associations), a polymorphic association would be required to allow one model to belong to several models. So I had to think for a minute: does it really make sense for this app that recipes belong to two different models? I really only want the categories as a way to separate recipes on the home page and allow users to search or filter based on category. I decided that the easiest approach would be to simply add a category column to the Recipes table.

Next, I had to update my `recipe_params` in the Recipe Controller to account for the addition of the category field. After this, I added the field to the related serializer. Finally, I wrote a class method in the Recipe model to create the categories users can choose from in the form.

After those things were taken care of on the back-end, I moved on to the views. This was fairly easy. I just added a drop down menu to the form. At first I had a little trouble. I got the drop down menu to show up okay, but it wouldn't add the category to the recipe. I quickly realized what my problem was: I was using `select_tag` but neglected one key component: the fact that I needed `f.select_tag` to wire it up to my form. Once I fixed that, everything started working!

## A Splash of Style

There really isn't a ton to say here, but I refreshed myself on Bootsrap. It had been a while since I actively used Bootstrap, so I had to do a lot of playing around to figure out what I was doing again. I got both my recipe form and the recipe show page styled the way I envisioned, and they both look very polished and clean. 

## Looking Ahead

I really have come a long way from where I left this project last year. I always knew I would come back to it and punch it up, but it feels good to finally be making some progress. But I'm not at the finish line yet. This is what I still need:

* **Home Page**: The home page is currently very plain. I want to add the categories I created as headers with their respective recipes underneath as cards. I also plan to incorporate jQuery to allow users to show and hide recipes on the page. For example, by default I might show four recipes for each category with an option to expand and/or hide. I also want to explore the possibility of using modals to give a preview of recipes, but this might not be necessary.
* **Vote**: I want people to be able to indicate whether they like or dislike a recipe. I need to play around with this and likely do some research to see if I can find a pattern that works with my project. Maybe this way I can avoid creating unnecessary migrations that I might need to remove later. 
* **User Profile**: This is important to give people a way to connect with each other. I never envisioned that I might create a social media site, but this might be a useful way for people to make meaningful connections over something we all love: food!

Those are the big things I will be working on. Of course, I will continue to update styles as I go along, so it wouldn't be surprising if the site looked even more transformed by my next post.
