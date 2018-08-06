---
layout: post
title:      "Refining A Recipe - Part 5"
date:       2018-08-06 06:20:46 +0000
permalink:  refining_a_recipe_-_part_5
---


I didn't get to finish adding voting capabilities to my app, but I was able to get other things accomplished. This week I focused on updating the Bootstrap styles. Up until this week, my app had been using the `bootstrap-sass` gem, but I wanted to take advantage of the updates made in Bootstrap 4. So I removed the gem, added the good ol' `bootstrap` gem, and then updated my styesheets to reflect the changes. The major change was deleting the `require tree` and editing `application.css` to `application.scss` and then adding `@import 'bootstrap`. In order to access my custom stylesheet, I also had to add `@import 'custom'`. 

For the most part, everything worked smoothly. One issue that I did encounter while making these updates came clear when I pushed the changes to Heroku. On my laptop, everything worked fine. But when I opened it up on my phone, I noticed a problem when trying to click on a link from the collapsable menu. The page wasn't reloading to the new page, and it was trying to load some JSON data. I wasn't sure what was going on, but the JSON was a clue that it might be something in my Javascript. I opened my JS file and found the function that was culprit. I scanned the function and found that it was being fired with a `div .show` was being clicked. I looked at the HTML and saw that the collapsable menu and saw that when the hamburger icon was clicked, it added `.show` to the div, and the JS function did what I told it do. Once I got rid of the function, it all started working again!

That's it for now!
